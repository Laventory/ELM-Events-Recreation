# ELM-Events-Recreation (Double Yolked Branch)
A recreation of the FMOD events for the Pizza Tower mod [**Egg's Lap Mod: Double Yolked**](https://gamebanana.com/mods/537351) as an FSPRO containing only those events/folders for those who want to use custom music and sounds with their own [Pizza Tower FMOD FSPRO recreations](https://github.com/Raltyro/PT-FSPRO-Recreation).

# How it works
The FMOD Project included here merely contains the folder structure and events that ELM reads for, in order for you to make it work with your own FMOD project all you must do is the following steps.


1. Open the FMOD project and copy the folders with the events inside into your own FMOD project.

![](https://i.postimg.cc/P5LvndG6/1.png)

2. Create two new banks in the "Banks" tab, these banks respectfully should be named `ELMmusic` and `ELMsfx`, alongside these rename `Master` to `ELMMaster`

![](https://i.postimg.cc/Kvp3WRWk/2.png)

3. Assign the folders to their respective banks.

![](https://i.postimg.cc/cJwK6TLw/3.png)

4. Assign the events in the mixer
  - You can open the mixer tab with CTRL+5, assign the music and sfx to their respective mixer folders.
   
![](https://i.postimg.cc/2SPbzgrC/4.png)

5. Set the state parameter to be "Exposed recursively via event instruments"
  - This allows the pizzatime event to actually reference the main Pizza Tower one and still function as it should, instead of needing to recreate the original event.

![](https://i.postimg.cc/pV4pQg5z/state.png)

6. If you are choosing to build for The Noise Update and you want Noise to have unique music, port over the `pizzatimenoise` event instead, and rename it to `pizzatime`.

7. Modify to your hearts content or build and put them in `Pizza Tower\sound\Desktop\_` and `Desktop\EggsLapMod\_` for the respective normal and ELM bank files.
  - You need not worry about creating a `Master.bank` or `Master.strings.bank` as ELM only reads the `ELMMaster.bank` and `ELMMaster.strings.bank` files that are in the EggsLapMod folder.

# Music Credits
- Vozaxhi - [Pillar John's Revenge](https://www.youtube.com/watch?v=MSzReOhnxXg)
- Inceptradom - Absolute AbsurZiti [V1 REDUX](https://www.youtube.com/watch?v=_x3RvXH7sdo) / [V2](https://www.youtube.com/watch?v=Tj6sN5GNBPA)
- LAAAAE - Funiculi Freakout [V1](https://www.youtube.com/watch?v=cr0Y_DkL05w) / [V1 REDUX](https://www.youtube.com/watch?v=vPA3co_iesA) / [V2](https://www.youtube.com/watch?v=NuDjZB65ViA)
- DimWiddy - [Memento Morinara](https://soundcloud.com/dimwiddy/memento-morinara)
- _sillicate - [How To Self-Destruct](https://www.youtube.com/watch?v=NA5yxiphq74)