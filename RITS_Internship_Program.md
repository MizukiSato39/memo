# RITS_Internship_Program
明日行う修正予定
- フォースセンサー用の関数の実装
- yellowを選択したとき以外の分岐の確認（青の誤認対策）
- 緑を読み取ったときの超音波センサー

## フォースセンサー用の関数
```python
from force_drive import ForceDriver
self.force_drv = ForceDriver(Port.S2)
def button_pressed():
	while True:
		button_check = self.force_drv.is_pressed_check()
		if button_check == True:
			self.motor_drv.back_and_reverse():
			break
		else:
			continue

	# while not self.force_drv.is_pressed():
	# ev3.screen.draw_text(0, 0, "Please press button")
	# self.motor_drv.back_and_reverse():


```

## Blueの誤認を防ぐ構文
```python
BlueCount = 0
if got_color is Color.WHITE:
	self.motor_drv.run(self.HIGH, self.LOW)
elif got_color is Color.BLUE:
	BlueCount += 1
	if seat_color is Color.BLUE and BlueCount > 10:
		break
	else:
		continue

else:
	self.motor_drv.run(self.LOW, self.HIGH)
	BlueCount += 0

```

## 緑を読み取ったときの障害物センサ
```python
def Green_to_Goal(self,seatColor):
	self.motor_drv.reset()
	distance_cm = 55
	distance = self.sonic_drv.get_distance()
	obnanndakakanndaka = 80
	deg_target = self.motor_drv.__calc_degree(distance_cm)
	self.motor_drv.reset()

	while True:
		while abs(self.motot_drv.left_motor.angle()) < deg_target:
			while distance <= obnanndakakanndaka:
				self.motor_drv.stop()
				wait(100)

			if got_color is Color.WHITE:
				self.motor_drv.run(self.HIGH, self.LOW)
			else:
				self.motor_drv.run(self.LOW, self.HIGH)

		self.motor_drv.turn(MotorDriver.LEFT,180)
		self.motor_drv.stop()
		break
```