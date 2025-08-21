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
{$USE file}
{$USE ini}
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
Dialog.AddButton(0@, 56, "OK", 215, 30@, 120, 40)
Dialog.AddButton(0@, 57, "Next page", 345, 30@, 120, 40)
Dialog.SetVisible(0@, 0)

Dialog.Create(3@, "Route selector       |       Page 2") 
Dialog.SetRECT(3@, 28@, 29@, 670, 595)
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
Dialog.AddCheckBox(3@, 28, "Palomino Creek", 10, 490, 300, 30)
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
Dialog.AddCheckBox(3@, 55 , "Palomino Creek", 345, 490, 300, 30)
Dialog.AddButton(3@, 56, "OK", 215, 525, 120, 40)
Dialog.AddButton(3@, 57, "Previous page", 345, 525, 120, 40)
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
0BE3: raknet setup_incoming_rpc_hook @timer_hook



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
int var_time
int var_test = 0
int var_index
longstring var_auxstring
longstring var_timestring
longstring var_extract
alloc var_index 10
alloc 22@ 256
alloc 23@ 256
22@ = #NULL
23@ = #NULL

0005: 20@ = -1
0005: 21@ = 26  
 
if 0B00: delete_file "cleo\cleo_saves\Auto Trucker - Routes List.ini"
then
end 

gosub @create_routes_list
 

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
        2@ == 56
        then
            Dialog.SetVisible(0@, 0)
            SAMP.ToggleCursor(0)
            0005: $aux = 20@
            if $aux == -1
            then
                22@ = #NULL
                chatmsg "{%x}<{%x}!{%x}> First route not selected" -1 __GRA __RED __GRA
            else
                0AB1: call_scm_func @route_lookup 1 $aux 22@
                free var_auxstring
                chatmsg "{%x}<{%x}!{%x}> Route 1 set to:{%x} %s" -1 __GRA __RED __GRA __WHT 22@
            end
            
            0005: $aux = 21@
            000C: $aux -= 27
            if $aux == -1
            then
                23@ = #NULL
                chatmsg "{%x}<{%x}!{%x}> Second route not selected" -1 __GRA __RED __GRA
            else
                0AB1: call_scm_func @route_lookup 1 $aux 23@
                free var_auxstring
                chatmsg "{%x}<{%x}!{%x}> Route 2 set to:{%x} %s" -1 __GRA __RED __GRA __WHT 23@
            end
        end
        
        if 2@ == 57
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
        2@ == 56
        then
            Dialog.SetVisible(3@, 0)
            SAMP.ToggleCursor(0)
            0005: $aux = 20@
            if $aux == -1
            then
                $route_1 = #NULL
                chatmsg "{%x}<{%x}!{%x}> First route not selected" -1 __GRA __RED __GRA
            else
                0AB1: call_scm_func @route_lookup 1 $aux 22@
                free var_auxstring
                chatmsg "{%x}<{%x}!{%x}> Route 1 set to:{%x} %s" -1 __GRA __RED __GRA __WHT 22@
            end
            
            0005: $aux = 21@
            000C: $aux -= 27
            if $aux == -1
            then
                $route_2 = #NULL
                chatmsg "{%x}<{%x}!{%x}> Second route not selected" -1 __GRA __RED __GRA
            else
                0AB1: call_scm_func @route_lookup 1 $aux 23@
                free var_auxstring
                chatmsg "{%x}<{%x}!{%x}> Route 2 set to:{%x} %s" -1 __GRA __RED __GRA __WHT 23@
            end
        end
        
        if 2@ == 57
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
        2@ < 29
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
        2@ < 56
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
            while TIMERA <= 70000
                wait 0
                var_time = TIMERA / 1000
                         
                var_time = 70 - var_time
                alloc var_timestring 100
                0AD3: var_timestring = format "Current job delay %ds" var_time
                alloc var_auxstring 100
                0AA8: call_function_method 6946896 struct 12694336 num_params 1 pop 0 'CRED601' var_auxstring 
                0AA5: call 7439872 num_params 2 pop 2 var_auxstring var_timestring
                free var_auxstring
                free var_timestring
                03F0: enable_text_draw 1
                033F: set_text_draw_letter_size 0.22 0.9 
                081C: draw_text_outline 1 RGBA 0 0 0 255 
                0340: set_text_draw_RGBA 65 255 144 255 
                0349: set_text_draw_font 1
                03E4: set_text_draw_align_right 1 
                033E: set_draw_text_position 128.0 330.0 GXT 'CRED601'
            end
            0AC9: free_allocated_memory $currentString
        end
        0AC9: free_allocated_memory 4@
    end
         
end    
jump @main_loop


:timer_hook
0BE5: raknet 28@ = get_hook_param PARAM_PACKETID
if 28@ == RPC_SCRCLIENTMESSAGE
then     
    0BE5: raknet 28@ = get_hook_param PARAM_BITSTREAM
    0BE7: raknet 27@ = bit_stream_read 28@ type BS_TYPE_INT
    0BE7: raknet 26@ = bit_stream_read 28@ type BS_TYPE_INT 
    26@++
    alloc 25@ 26@
    0C11: memset destination 25@ value 0 size 26@
    26@-- 
    0BE8: raknet bit_stream 28@ read_array 25@ size 26@
    0C0D: struct 25@ offset 26@ size 1 = 0 
    
    if
    0C29: -1 = stristr string1 25@ string2 "Mergi la checkpoint-ul de pe mapa pentru a alege o noua ruta."
    then
        TIMERA = 0
        0BE0: raknet hook_ret true
    end
    free 25@
end
0BE0: raknet hook_ret true

:trucker
if 0B4C: samp is_dialog_active -1
then
else
    Dialog.SetVisible(0@, 1)
end
SAMP.CmdRet()


:create_routes_list
alloc 10@ 20000
0AC6: 10@ = label @routes_list offset
0C16: var_extract = strtok string1 10@ string2 ";"
var_index = 0                      
alloc 11@ 50
while not var_extract == #NULL
    var_index++
    0AD3: 11@v = format "route%d" var_index
    0AF5: write_string var_extract to_ini_file "cleo\cleo_saves\Auto Trucker - Routes List.ini" section "routes" key 11@v
    0C16: var_extract = strtok string1 #NULL string2 ";"
end
free 10@
free 11@
return

:routes_list
hex 
4D 69 64 6E 69 67 68 74 20 43 61 72 67 6F 3B 53 68 61 64 6F 77 20 46 72 65 69 67 68 74 3B 42 6C 61 63 6B 20 42 6F 78 20 44 65 6C 69 76 65 72 79 3B 50 68 61 6E 74 6F 6D 20 53 68 69 70 6D 65 6E 74 3B 53 69 6C 65 6E 74 20 50 61 63 6B 61 67 65 3B 43 6F 6C 64 20 43 68 61 69 6E 20 54 72 61 6E 73 70 6F 72 74 3B 4F 62 73 69 64 69 61 6E 20 46 72 65 69 67 68 74 3B 53 69 6C 76 65 72 20 4D 69 73 74 20 44 65 6C 69 76 65 72 79 3B 54 77 69 6C 69 67 68 74 20 43 6F 6E 73 69 67 6E 6D 65 6E 74 3B 4C 53 20 50 69 7A 7A 61 20 44 65 6C 69 76 65 72 79 3B 4C 53 20 38 20 54 72 61 63 6B 3B 4C 53 20 43 68 6F 70 20 53 68 6F 70 3B 4C 53 20 43 72 61 63 6B 20 48 6F 75 73 65 3B 4C 53 20 47 61 73 20 53 74 61 74 69 6F 6E 3B 56 69 6E 65 77 6F 6F 64 20 4D 61 72 6B 65 74 20 54 65 72 6D 69 6E 61 6C 3B 4C 56 20 47 61 73 20 53 74 61 74 69 6F 6E 3B 4C 56 20 43 6C 6F 74 68 69 6E 67 20 53 74 6F 72 65 3B 4C 56 20 42 75 72 67 65 72 20 53 68 6F 74 3B 4C 56 20 50 6F 6F 6C 3B 4C 56 20 50 69 72 61 74 65 20 53 68 69 70 3B 4C 56 20 43 68 75 63 6B 75 70 3B 43 6F 73 74 61 6C 20 4D 61 72 6B 65 74 3B 43 68 69 6C 69 61 64 20 53 68 61 64 6F 77 20 44 65 6E 3B 48 61 72 62 6F 72 20 53 46 20 47 61 73 20 53 74 61 74 69 6F 6E 3B 46 6F 72 74 20 43 61 72 73 6F 6E 20 43 6C 65 61 6E 69 6E 67 20 26 20 4C 61 75 6E 64 72 79 3B 44 75 73 74 79 20 54 72 61 69 6C 73 20 48 69 64 65 6F 75 74 3B 4E 6F 72 74 68 20 4D 61 72 6B 65 74 3B 50 61 6C 6F 6D 69 6E 6F 20 43 72 65 65 6B 3B
00
end

:route_lookup
var_index = 0@
alloc 11@ 50
0AD3: 11@v = format "route%d" var_index
alloc var_auxstring 256
0AF4: var_auxstring = read_string_from_ini_file "cleo\cleo_saves\Auto Trucker - Routes List.ini" section "routes" key 11@v
free 11@
0AB2: ret 1 var_auxstring    


```
</details>
