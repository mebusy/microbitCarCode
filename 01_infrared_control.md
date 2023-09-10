

```python
def on_ir_button_released():
    global IR_var
    IR_var = 0
makerbit.on_ir_button(IrButton.ANY, IrButtonAction.RELEASED, on_ir_button_released)

def on_ir_button_left_pressed():
    global IR_var
    IR_var = 3
makerbit.on_ir_button(IrButton.LEFT,
    IrButtonAction.PRESSED,
    on_ir_button_left_pressed)

def on_ir_button_down_pressed():
    global IR_var
    IR_var = 2
makerbit.on_ir_button(IrButton.DOWN,
    IrButtonAction.PRESSED,
    on_ir_button_down_pressed)

def on_ir_button_up_pressed():
    global IR_var
    IR_var = 1
makerbit.on_ir_button(IrButton.UP, IrButtonAction.PRESSED, on_ir_button_up_pressed)

def on_ir_button_right_pressed():
    global IR_var
    IR_var = 4
makerbit.on_ir_button(IrButton.RIGHT,
    IrButtonAction.PRESSED,
    on_ir_button_right_pressed)

def on_ir_button_ok_pressed():
    global IR_var
    IR_var = 5
makerbit.on_ir_button(IrButton.OK, IrButtonAction.PRESSED, on_ir_button_ok_pressed)

IR_var = 0
makerbit.connect_ir_receiver(DigitalPin.P8, IrProtocol.NEC)

def on_forever():
    if IR_var == 1:
        cbit_小车类.alone_ctrl_speed(cbit_小车类.AloneState.LEFT_Z_MOTOR, 120)
        cbit_小车类.alone_ctrl_speed(cbit_小车类.AloneState.RIGHT_Z_MOTOR, 135)
    elif IR_var == 2:
        cbit_小车类.alone_ctrl_speed(cbit_小车类.AloneState.LEFT_F_MOTOR, 120)
        cbit_小车类.alone_ctrl_speed(cbit_小车类.AloneState.RIGHT_F_MOTOR, 155)
    elif IR_var == 3:
        cbit_小车类.alone_ctrl_speed(cbit_小车类.AloneState.LEFT_Z_MOTOR, 0)
        cbit_小车类.alone_ctrl_speed(cbit_小车类.AloneState.RIGHT_Z_MOTOR, 138)
    elif IR_var == 4:
        cbit_小车类.alone_ctrl_speed(cbit_小车类.AloneState.LEFT_Z_MOTOR, 120)
        cbit_小车类.alone_ctrl_speed(cbit_小车类.AloneState.RIGHT_Z_MOTOR, 0)
    else:
        cbit_小车类.car_ctrl(cbit_小车类.CarState.CAR_STOP)
basic.forever(on_forever)

```


