

```javascript
makerbit.onIrButton(IrButton.Any, IrButtonAction.Released, function () {
    IR_var = 0
})
makerbit.onIrButton(IrButton.Left, IrButtonAction.Pressed, function () {
    IR_var = 3
})
makerbit.onIrButton(IrButton.Down, IrButtonAction.Pressed, function () {
    IR_var = 2
})
makerbit.onIrButton(IrButton.Up, IrButtonAction.Pressed, function () {
    IR_var = 1
})
makerbit.onIrButton(IrButton.Right, IrButtonAction.Pressed, function () {
    IR_var = 4
})
makerbit.onIrButton(IrButton.Ok, IrButtonAction.Pressed, function () {
    IR_var = 5
})
let IR_var = 0
makerbit.connectIrReceiver(DigitalPin.P8, IrProtocol.NEC)
IR_var = 0
basic.forever(function () {
    if (IR_var == 1) {
        if (cbit_小车类.Ultrasonic_Car() < 20) {
            cbit_小车类.CarCtrl(cbit_小车类.CarState.Car_Stop)
            music.play(music.createSoundExpression(WaveShape.Square, 200, 1, 255, 0, 100, SoundExpressionEffect.None, InterpolationCurve.Curve), music.PlaybackMode.InBackground)
        } else {
            cbit_小车类.AloneCtrlSpeed(cbit_小车类.AloneState.Left_Z_Motor, 120)
            cbit_小车类.AloneCtrlSpeed(cbit_小车类.AloneState.Right_Z_Motor, 135)
        }
    } else if (IR_var == 2) {
        cbit_小车类.AloneCtrlSpeed(cbit_小车类.AloneState.Left_F_Motor, 120)
        cbit_小车类.AloneCtrlSpeed(cbit_小车类.AloneState.Right_F_Motor, 155)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Quarter)), music.PlaybackMode.InBackground)
    } else if (IR_var == 3) {
        cbit_小车类.AloneCtrlSpeed(cbit_小车类.AloneState.Left_Z_Motor, 0)
        cbit_小车类.AloneCtrlSpeed(cbit_小车类.AloneState.Right_Z_Motor, 120)
    } else if (IR_var == 4) {
        cbit_小车类.AloneCtrlSpeed(cbit_小车类.AloneState.Left_Z_Motor, 120)
        cbit_小车类.AloneCtrlSpeed(cbit_小车类.AloneState.Right_Z_Motor, 0)
    } else {
        cbit_小车类.CarCtrl(cbit_小车类.CarState.Car_Stop)
    }
})
```
