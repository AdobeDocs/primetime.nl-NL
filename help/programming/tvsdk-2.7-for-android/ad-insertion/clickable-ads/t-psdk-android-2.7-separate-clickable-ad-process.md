---
description: U moet de gebruikersinterfacelogica van uw speler scheiden van het proces dat beheert en klikt. Een manier om dit te doen is het implementeren van meerdere fragmenten voor een activiteit.
title: Scheid het klikbare ad proces
exl-id: 9b6fad9b-d46d-4965-8770-0bb85c052e0e
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Scheid het klikbare ad proces {#separate-the-clickable-ad-process}

U moet de gebruikersinterfacelogica van uw speler scheiden van het proces dat beheert en klikt. Een manier om dit te doen is het implementeren van meerdere fragmenten voor een activiteit.

1. Eén fragment implementeren dat de `MediaPlayer`.

   Dit fragment moet worden aangeroepen `notifyClick()` en is verantwoordelijk voor het afspelen van video.

   ```java
   public class PlayerFragment extends SherlockFragment { 
       ... 
       public void notifyAdClick () { 
           _mediaPlayer.notifyClick(); 
       } 
       ... 
   } 
   ```

1. Voer een verschillend fragment uit om een element te tonen UI dat erop wijst dat een advertentie klikbaar is, dat element controleert UI, en gebruiker aan het fragment meedelen dat bevat `MediaPlayer`.

   Dit fragment moet een interface voor fragmentcommunicatie declareren. Het fragment legt de interface-implementatie vast tijdens de installatie `onAttach()` levenscyclusmethode en kan de interfacemethodes roepen om met de activiteit te communiceren.

   ```java
   public class PlayerClickableAdFragment extends SherlockFragment { 
       private ViewGroup viewGroup; 
       private Button button; 
       OnAdUserInteraction callback; 
       @Override 
       public View onCreateView(LayoutInflater inflater,  
                                ViewGroup container,  
                                Bundle savedInstanceState) { 
           // the custom fragment is defined by a custom button 
           viewGroup = (ViewGroup) inflater.inflate(R.layout.fragment_player_clickable_ad,  
                                                    container, false); 
           button = (Button) viewGroup.findViewById(R.id.clickButton); 
   
           // register a click listener to detect user interaction 
           button.setOnClickListener(new View.OnClickListener() { 
               @Override 
               public void onClick(View v) { 
                   // send the event back to the activity 
                   callback.onAdClick(); 
               } 
           }); 
           viewGroup.setVisibility(View.INVISIBLE); 
           return viewGroup; 
       } 
   
       public void hide() { 
           viewGroup.setVisibility(View.INVISIBLE); 
       } 
   
       public void show() { 
           viewGroup.setVisibility(View.VISIBLE);     
       } 
   
       @Override 
       public void onAttach(Activity activity) { 
           super.onAttach(activity); 
           // attaches the interface implementation 
           // if the container activity does not implement the methods  
           // from the interface an exception will be thrown 
           try { 
               callback = (OnAdUserInteraction) activity; 
           } catch (ClassCastException e) { 
               throw new ClassCastException(activity.toString() 
                   + " must implement OnAdUserInteraction"); 
           }     
       } 
   
       // user defined interface that allows fragment communication 
       // must be implemented by the container activity 
       public interface OnAdUserInteraction { 
           public void onAdClick(); 
       } 
   } 
   ```
