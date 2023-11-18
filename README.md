# ELM-Events-Recreation
A very rough recreation of the FMOD event folders as a project for the Pizza Tower mod [**Egg's Lap Mod**](https://gamebanana.com/mods/464912) for those who want to use custom music and sounds with their own Pizza Tower [FMOD](https://gamebanana.com/tools/13432) [recreations](https://github.com/Laventory/CheesedUP-FMOD).

# How it works
The FMOD Project included here merely contains the folder structure and events that ELM reads for, in order for you to make it work with your own FMOD project all you must do is the following steps.


1. Open the FMOD project and copy the folders with the events inside into your own FMOD project.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1175285747125850202/image.png)

2. Create two new banks in the "Banks" tab, these banks respectfully should be named `ELMmusic` and `ELMsfx`, alongside these rename `Master` to `ELMMaster`

![](https://cdn.discordapp.com/attachments/1140611242411700297/1175289796025909369/image.png)

3. Assign the folders to their respective banks.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1175291221120397352/image.png)

4. Assign the events in the mixer
> You can open the mixer tab with CTRL+5, assign the music and sfx to their respective mixer folders.
   
![](https://cdn.discordapp.com/attachments/1140611242411700297/1175461476635525120/image.png)

5. Modify to your hearts content or build and put them in `Pizza Tower\sound\Desktop\_` and `Desktop\EggsLapMod\_` for the respective ELM and normal bank files.
> You need not worry about creating a `Master.bank` or `Master.strings.bank` as ELM only reads the `ELMMaster.bank` and `ELMMaster.strings.bank` files that are in the EggsLapMod folder.