# tiny tapeout vga bullet hell demo

this is a simple bullet hell mini game made in verilog for tiny tapeout. you control a little player trying to dodge bullets coming down from a rocket boss moving side to side at the top.

there is a timer on the top right counting how many seconds you survive. if you get hit, screen turns red and game over.

## controls

uses the inputs on `ui_in`:

* `ui_in[0]` - up
* `ui_in[1]` - down
* `ui_in[2]` - left
* `ui_in[3]` - right
* `ui_in[4]` - restart game

## modules

* `tt_um_vga_example` - top level wrapper, syncs the button inputs and outputs 6-bit color + vga sync signals on `uo_out`
* `vga_sync` - generates 640x480 standard vga timing signals (hsync, vsync) and pixel coordinates
* `game_logic` - handles player movement, rocket boss movement, 4 bullet streams, timer, hitboxes and game over state
* `pixel_gen` - draws everything on screen (player circle, rocket boss shape, bullets, background, and 7-segment timer)

## parameters

* `PIXEL_DIV`: set to 1 for vga playground pixel clock, or set to 4 if running on 100MHz fpga like basys 3
* `TIMER_FRAMES_PER_SECOND`: default is 36 fps for simulation, change to 60 for real hardware operation
