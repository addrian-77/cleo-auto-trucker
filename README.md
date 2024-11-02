# Auto Trucker
**Pentru a descarca modul, apasati pe butonul <>Code, iar apoi pe Download ZIP**
#

> Modul a fost facut cu CLEO 4.1.1.30 si SAMPFUNCS 5.4.0, nu am testat compatibilitate pentru alte versiuni.

### **Lista cu comenzi:**

- **/trucker** pentru a activa sau dezactiva modul

### Mod de folosire:
> Folositi comanda /trucker pentru a alege 2 rute, daca nu e niciuna (sau doar una) selectata atunci modul este oprit.

### Instalare

Pentru instalare descarcati arhiva "auto.trucker.rar" si trageti folderul "cleo" peste folderul principal al jocului. Asigurati-va ca in folderul cleo aveti "routes.txt" si "trucker autoselect.cs", altfel modul nu va functiona.

### Screenshot:
![image](https://github.com/user-attachments/assets/11aaff82-42f9-499c-a57a-8982846665bd)

<details>
<summary>Codul sursa:</summary>

```cpp
{$CLEO}
{$INCLUDE SF}

0000:


repeat
wait 0
until SAMP.Available()


Dialog.Create(0@, "Route selector       |       Page 1")
SAMP.GetScreenResolution(28@, 29@)
if 29@ < 650
then
    30@ = 350
else
    30@ = 590
end
28@ /= 2 
29@ /= 2 
28@ -= 335 
29@ -= 330
Dialog.SetRECT(0@, 28@, 29@, 670, 650)
Dialog.SetBackgroundColor(0@, -1090519040)
Dialog.AddStatic(0@, 37, "New ILLEGAL routes:", 10, 0, 200, 40)
Dialog.AddCheckBox(0@, 1, "Midnight Cargo", 10, 35, 300, 30)
Dialog.AddCheckBox(0@, 2, "Shadow Freight", 10, 70, 300, 30)
Dialog.AddCheckBox(0@, 3, "Black Box Delivery", 10, 105, 300, 30)
Dialog.AddCheckBox(0@, 4, "Phantom Shipment", 10, 140, 300, 30)
Dialog.AddCheckBox(0@, 5, "Silent Package", 10, 175, 300, 30)
Dialog.AddCheckBox(0@, 6, "Cold Chain Transport", 10, 210, 300, 30)
Dialog.AddCheckBox(0@, 7, "Obsidian Freight", 10, 245, 300, 30)
Dialog.AddCheckBox(0@, 8, "Silver Mist Delivery", 10, 280, 300, 30)
Dialog.AddCheckBox(0@, 9, "Twilight Consignment", 10, 315, 300, 30)
Dialog.AddStatic(0@, 37, "Los Santos:", 10, 350, 120, 40)
Dialog.AddCheckBox(0@, 10, "LS Pizza Delivery", 10, 385, 300, 30)
Dialog.AddCheckBox(0@, 11, "LS 8 Track", 10, 420, 300, 30)
Dialog.AddCheckBox(0@, 12, "LS Chop Shop", 10, 455, 300, 30)
Dialog.AddCheckBox(0@, 13, "LS Crack House", 10, 490, 300, 30)
Dialog.AddCheckBox(0@, 14, "LS Gas Station", 10, 525, 300, 30)
Dialog.AddCheckBox(0@, 15, "Vinewood Market Terminal", 10, 560, 300, 30)
Dialog.AddStatic(0@, 37, "New ILLEGAL routes:", 345, 0, 200, 40)
Dialog.AddCheckBox(0@, 28, "Midnight Cargo", 345, 35, 300, 30)
Dialog.AddCheckBox(0@, 29, "Shadow Freight", 345, 70, 300, 30)
Dialog.AddCheckBox(0@, 30, "Black Box Delivery", 345, 105, 300, 30)
Dialog.AddCheckBox(0@, 31, "Phantom Shipment", 345, 140, 300, 30)
Dialog.AddCheckBox(0@, 32, "Silent Package", 345, 175, 300, 30)
Dialog.AddCheckBox(0@, 33, "Cold Chain Transport", 345, 210, 300, 30)
Dialog.AddCheckBox(0@, 34, "Obsidian Freight", 345, 245, 300, 30)
Dialog.AddCheckBox(0@, 35, "Silver Mist Delivery", 345, 280, 300, 30)
Dialog.AddCheckBox(0@, 36, "Twilight Consignment", 345, 315, 300, 30)
Dialog.AddStatic(0@, 37, "Los Santos:", 345, 350, 120, 40)
Dialog.AddCheckBox(0@, 37, "LS Pizza Delivery", 345, 385, 300, 30)
Dialog.AddCheckBox(0@, 38, "LS 8 Track", 345, 420, 300, 30)
Dialog.AddCheckBox(0@, 39, "LS Chop Shop", 345, 455, 300, 30)
Dialog.AddCheckBox(0@, 40, "LS Crack House", 345, 490, 300, 30)
Dialog.AddCheckBox(0@, 41, "LS Gas Station", 345, 525, 300, 30)
Dialog.AddCheckBox(0@, 42, "Vinewood Market Terminal", 345, 560, 300, 30)
Dialog.AddButton(0@, 55, "OK", 215, 30@, 120, 40)
Dialog.AddButton(0@, 56, "Next page", 345, 30@, 120, 40)
Dialog.SetVisible(0@, 0)

Dialog.Create(3@, "Route selector       |       Page 2") 
Dialog.SetRECT(3@, 28@, 29@, 670, 560)
Dialog.SetBackgroundColor(3@, -1090519040)
Dialog.AddStatic(3@, 38, "Las Venturas:", 10, 0, 120, 40)
Dialog.AddCheckBox(3@, 16, "LV Gas Station", 10, 35, 300, 30)
Dialog.AddCheckBox(3@, 17, "LV Clothing Store", 10, 70, 300, 30)
Dialog.AddCheckBox(3@, 18, "LV Burger Shot", 10, 105, 300, 30)
Dialog.AddCheckBox(3@, 19, "LV Pool", 10, 140, 300, 30)
Dialog.AddCheckBox(3@, 20, "LV Pirate Ship", 10, 175, 300, 30)
Dialog.AddCheckBox(3@, 21, "LV Chuckup", 10, 210, 300, 30)
Dialog.AddStatic(3@, 37, "San Fierro:", 10, 245, 120, 40)
Dialog.AddCheckBox(3@, 22, "Costal Market", 10, 280, 300, 30)
Dialog.AddCheckBox(3@, 23, "Chiliad Shadow Den", 10, 315, 300, 30)
Dialog.AddCheckBox(3@, 24, "Harbor SF Gas Station", 10, 350, 300, 30)
Dialog.AddCheckBox(3@, 25, "Fort Carson Cleaning & Laundry", 10, 385, 300, 30)
Dialog.AddCheckBox(3@, 26, "Dusty Trails Hideout", 10, 420, 300, 30)
Dialog.AddCheckBox(3@, 27, "North Market", 10, 455, 300, 30)
Dialog.AddStatic(3@, 38, "Las Venturas:", 345, 0, 120, 40)
Dialog.AddCheckBox(3@, 43, "LV Gas Station", 345, 35, 300, 30)
Dialog.AddCheckBox(3@, 44, "LV Clothing Store", 345, 70, 300, 30)
Dialog.AddCheckBox(3@, 45, "LV Burger Shot", 345, 105, 300, 30)
Dialog.AddCheckBox(3@, 46, "LV Pool", 345, 140, 300, 30)
Dialog.AddCheckBox(3@, 47, "LV Pirate Ship", 345, 175, 300, 30)
Dialog.AddCheckBox(3@, 48, "LV Chuckup", 345, 210, 300, 30)
Dialog.AddStatic(3@, 37, "San Fierro:", 345, 245, 120, 40)
Dialog.AddCheckBox(3@, 49, "Costal Market", 345, 280, 300, 30)
Dialog.AddCheckBox(3@, 50, "Chiliad Shadow Den", 345, 315, 300, 30)
Dialog.AddCheckBox(3@, 51, "Harbor SF Gas Station", 345, 350, 300, 30)
Dialog.AddCheckBox(3@, 52, "Fort Carson Cleaning & Laundry", 345, 385, 300, 30)
Dialog.AddCheckBox(3@, 53, "Dusty Trails Hideout", 345, 420, 300, 30)
Dialog.AddCheckBox(3@, 54, "North Market", 345, 455, 300, 30)
Dialog.AddButton(3@, 55, "OK", 215, 490, 120, 40)
Dialog.AddButton(3@, 56, "Previous page", 345, 490, 120, 40)
Dialog.SetVisible(3@, 0)

const
    __BLU = 0x268efc
    __RED = 0xff2b2b
    __YLW = 0xffeb0f
    __WHT = 0xffffff
    __GRN = 0x4ae072
    __OLV = 0xc3e820
    __GRA = 0xcfcfcf
end

const
    EVENT_BUTTON_CLICKED                = 257
    EVENT_COMBOBOX_SELECTION_CHANGED    = 513
    EVENT_RADIOBUTTON_CHANGED           = 769
    EVENT_CHECKBOX_CHANGED              = 1025
    EVENT_SLIDER_VALUE_CHANGED          = 1281
    EVENT_EDITBOX_STRING                = 1537
    EVENT_EDITBOX_CHANGE                = 1538
    EVENT_LISTBOX_ITEM_DBLCLK           = 1793
    EVENT_LISTBOX_SELECTION             = 1794
end

chatmsg "{%x}Auto Trucker {%x}mod by {%x}iAdriaN {%x}was loaded." -1 __WHT __OLV __WHT __OLV
chatmsg "{%x}Use {%x}[/trucker] {%x}to toggle the mod {%x}ON {%x}or {%x}OFF." -1 __GRA __YLW __GRA __GRN __GRA __RED             
0B34: samp register_client_command "trucker" to_label @trucker



var
    $cnt_1: int
    $cnt_2: int
    $last_1: int
    $selected_1: int
    $last_2: int
    $selected_2: int
    $aux: int
    3@: string
    $current: int
    $found: int
    $currentString: string
    $extract: string
    $auxlen: int
    $selected: int
end
0AC8: 22@ = allocate_memory_size 260
0AC8: 23@ = allocate_memory_size 260
22@ = #NULL
23@ = #NULL

0005: 20@ = -1
0005: 21@ = 26  
 

:main_loop

wait 0    
if 
Dialog.IsVisible(0@)
then
    SAMP.ToggleCursor(1)
    0B81: dialog 0@ pop_event_to 1@ control_id_to 2@
    if
    1@ == EVENT_BUTTON_CLICKED
    then
        if
        2@ == 55
        then
            Dialog.SetVisible(0@, 0)
            SAMP.ToggleCursor(0)
            0005: $aux = 20@
            if $aux == -1
            then
                22@ = #NULL
                chatmsg "{%x}<{%x}!{%x}> First route not selected" -1 __GRA __RED __GRA
            else
                0AB1: call_scm_func @get_route 1 $aux 22@
                0C17: $auxlen = strlen 22@
                $auxlen -= 1
                0C24: strncpy destination 22@ source 22@ size $auxlen
                chatmsg "{%x}<{%x}!{%x}> Route 1 set to:{%x} %s" -1 __GRA __RED __GRA __WHT 22@
            end
            
            0005: $aux = 21@
            000C: $aux -= 27
            if $aux == -1
            then
                23@ = #NULL
                chatmsg "{%x}<{%x}!{%x}> Second route not selected" -1 __GRA __RED __GRA
            else
                0AB1: call_scm_func @get_route 1 $aux 23@
                0C17: $auxlen = strlen 23@
                $auxlen -= 1
                0C24: strncpy destination 23@ source 23@ size $auxlen
                chatmsg "{%x}<{%x}!{%x}> Route 2 set to:{%x} %s" -1 __GRA __RED __GRA __WHT 23@
            end
        end
        
        if 2@ == 56
        then
            Dialog.SetVisible(0@, 0)
            Dialog.SetVisible(3@, 1)
        end           
    end
    
    if
    1@ == EVENT_CHECKBOX_CHANGED
    then
        if and
        2@ > 0
        2@ < 28
        then
            $selected_2 = 21@ - 27
            if 0038: 2@ == $selected_2
            then
                print "You can't select the same route" 1000
                0B9E: dialog 0@ checkbox 2@ set_checked 0
            else
                if 0038: 2@ == 20@ // (int)
                then
                    20@ = -1
                else
                    0B9E: dialog 0@ checkbox 20@ set_checked 0
                    0B9E: dialog 3@ checkbox 20@ set_checked 0
                    0005: 20@ = 2@                                                 
                end
            end
        end
        if and
        2@ > 27
        2@ < 55
        then
            $selected_1 = 20@ + 27
            if 0038: 2@ == $selected_1
            then
                print "You can't select the same route" 1000
                0B9E: dialog 0@ checkbox 2@ set_checked 0
            else
                if 0038: 2@ == 21@
                then
                    21@ = 26
                else
                    0B9E: dialog 0@ checkbox 21@ set_checked 0
                    0B9E: dialog 3@ checkbox 21@ set_checked 0
                    0005: 21@ = 2@
                end
            end
        end
    end
    
end

if 
Dialog.IsVisible(3@)
then
    SAMP.ToggleCursor(1)
    0B81: dialog 3@ pop_event_to 1@ control_id_to 2@
    if
    1@ == EVENT_BUTTON_CLICKED
    then
        if
        2@ == 55
        then
            Dialog.SetVisible(3@, 0)
            SAMP.ToggleCursor(0)
            0005: $aux = 20@
            if $aux == -1
            then
                $route_1 = #NULL
                chatmsg "{%x}<{%x}!{%x}> First route not selected" -1 __GRA __RED __GRA
            else
                0AB1: call_scm_func @get_route 1 $aux 22@
                0C17: $auxlen = strlen 22@
                $auxlen -= 1
                0C24: strncpy destination 22@ source 22@ size $auxlen
                chatmsg "{%x}<{%x}!{%x}> Route 1 set to:{%x} %s" -1 __GRA __RED __GRA __WHT 22@
            end
            
            0005: $aux = 21@
            000C: $aux -= 27
            if $aux == -1
            then
                $route_2 = #NULL
                chatmsg "{%x}<{%x}!{%x}> Second route not selected" -1 __GRA __RED __GRA
            else
                0AB1: call_scm_func @get_route 1 $aux 23@
                0C17: $auxlen = strlen 23@
                $auxlen -= 1
                0C24: strncpy destination 23@ source 23@ size $auxlen
                chatmsg "{%x}<{%x}!{%x}> Route 2 set to:{%x} %s" -1 __GRA __RED __GRA __WHT 23@
            end
        end
        
        if 2@ == 56
        then
            Dialog.SetVisible(3@, 0)
            Dialog.SetVisible(0@, 1)
        end           
    end
    
    if
    1@ == EVENT_CHECKBOX_CHANGED
    then
        if and
        2@ > 0
        2@ < 28
        then
            $selected_2 = 21@ - 27
            if 0038: 2@ == $selected_2
            then
                print "You can't select the same route" 1000
                0B9E: dialog 3@ checkbox 2@ set_checked 0
            else
                if 0038: 2@ == 20@ // (int)
                then
                    20@ = -1
                else
                    0B9E: dialog 0@ checkbox 20@ set_checked 0
                    0B9E: dialog 3@ checkbox 20@ set_checked 0
                    0005: 20@ = 2@                                                 
                end
            end
        end
        if and
        2@ > 27
        2@ < 55
        then
            $selected_1 = 20@ + 27
            if 0038: 2@ == $selected_1
            then
                print "You can't select the same route" 1000
                0B9E: dialog 3@ checkbox 2@ set_checked 0
            else
                if 0038: 2@ == 21@
                then
                    21@ = 26
                else
                    0B9E: dialog 0@ checkbox 21@ set_checked 0
                    0B9E: dialog 3@ checkbox 21@ set_checked 0
                    0005: 21@ = 2@
                end
            end
        end   
    end
    
end

//cursa legala: Trucker: Choose Route
//confirm cusa legala: Trucker

//la fel pentru ilegala

if 
0B4C: samp is_dialog_active -1
then
    0AC8: 4@ = allocate_memory_size 260
    0BD8: samp get_dialog_caption 4@
    if 0C29: 4@ = stristr string1 4@ string2 "Choose Route"
    then
        if and
        not 22@ == #NULL
        not 23@ == #NULL
        then
            0B4E: samp 5@ = get_current_dialog_id   
            0AC8: $currentString = allocate_memory_size 2048
            0BD7: samp get_dialog_text $currentString
            0C16: $extract = strtok string1 $currentString string2 "-"
            $current = 0
            0B49: samp set_current_dialog_list_item $current
            while not $extract == #NULL
                if
                0C29: $NOT_USED = stristr string1 $extract string2 22@
                then
                    0B47: samp close_current_dialog_with_button 1
                    repeat
                        wait 0
                    until 0B4C: samp is_dialog_active -1
                    0B47: samp close_current_dialog_with_button 1
                    break
                end
                if
                0C29: $NOT_USED = stristr string1 $extract string2 23@
                then
                    0B47: samp close_current_dialog_with_button 1
                    repeat
                        wait 0
                    until 0B4C: samp is_dialog_active -1
                    0B47: samp close_current_dialog_with_button 1
                    break
                end
                if 0C16: $extract = strtok string1 #NULL string2 "-"
                then
                    $current ++
                    0B49: samp set_current_dialog_list_item $current
                end
            end
            0AC9: free_allocated_memory $currentString
        end
        0AC9: free_allocated_memory 4@
    end
         
end    
jump @main_loop

:get_route
if
0AAB:   file_exists "CLEO/routes.txt"
then
    if
    0A9A: 30@ = openfile "CLEO/routes.txt" mode "rt"  // IF and SET
    then
        10@ = 0
        alloc 31@ 20000
            while 0AD7: read_string_from_file 30@ to 31@ size 20000 // retrieves data from a file into a buffer until it encounters a new line
            wait 0
                10@++
                if
                003B:   10@ == 0@  // (int)
                then
                    0AB2: ret 1 31@
                end
            end
        free 31@
        0A9B: closefile 30@
    else
        0AD1: show_formatted_text_highpriority "Couldn't open the file" 15000
    end
else
    0AD1: show_formatted_text_highpriority "File doesn't exist" 15000
end

:trucker
if 0B4C: samp is_dialog_active -1
then
else
    Dialog.SetVisible(0@, 1)
end

SAMP.CmdRet()

```
</details>
