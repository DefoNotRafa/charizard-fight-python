# charizard-fight-python
epic battle with charizard
include everything below this text to play






	from colorama import init
init(convert=True)
def bossfight():
	import random
	import time
	RED = "\033[91m"
	GREEN = "\033[92m"
	YELLOW = "\033[93m"
	BLUE = "\033[94m"
	RESET = "\033[0m"
	myhp = 100
	BossHp = 135

	print(f"{RED} a wild charizard has appeared {RESET} ")

	print(
		f"print {GREEN} 'attack/heal'{RESET} to do action, print {RED} 'ATTACK/HEAL'{RESET} to do a stronger version of both actions with a chance of the action failing"
	)
	
	while myhp > 0 and BossHp > 0:
		print(f"Your HP: {GREEN} {myhp}{RESET} Boss HP: {RED} {BossHp}{RESET}")
		action = input(
			f"Choose Action: {YELLOW} attack/ATTACK or {YELLOW} heal/HEAL{RESET} "
		)
		# your attack
		if action == "attack":
			damage = random.randint(15, 25)
	
			BossHp = BossHp - damage
	
			print(
				f"{YELLOW} you lift your sword and voilently swing at the charizard{RESET}"
			)
			time.sleep(0.6)
			print("SWOOSH")
			if damage > 20:
				print(f"{YELLOW} Lucky. strong attack{RESET}")
			elif damage < 10:
				print(f"{YELLOW} Unlucky. weak attack {RESET}")
			print(
				f"{RED} {damage} damage to Charizard, Charizard now has:{BossHp}HP left{RESET}"
			)
		elif action == "ATTACK":
			if random.randint(1, 3) == 1:
				print("you missed")
			else:
				damage = random.randint(30, 50)
				print(f"{BLUE} ...")
				time.sleep(2)
				print(
					f"you feel a sudden charge inside of you. You place one foot down, stretch your sword behind and swing as hard as you can.{RESET} "
				)
				time.sleep(3)
	
				time.sleep(1)
				print(f"{YELLOW} SSWWWWWOOOOOOOSSSSHHHHH")
	
				BossHp = BossHp - damage
				print(
					f"Charizard has taken a heavy blow and lost{RED} {damage}{YELLOW} Hp, Charizard now has{RED} {BossHp} {RESET} HP left"
				)
	
			# your heal
		elif action == "heal":
			HealAmount = random.randint(10, 20)
			myhp = HealAmount + myhp
	
			print(
				f"{YELLOW} you grab a small bottle of a strange blue liquid and drink it{RESET} "
			)
			time.sleep(2)
			print(
				f"you healed {GREEN} {HealAmount} HP {RESET} back. you now have {myhp}{RESET} "
			)
		elif action == "HEAL":
			if random.randint(1, 2) == 1:
				print("you couldnt find the big potion")
			else:
				print("...")
				time.sleep(2)
				print(
					"you grab to your hidden pocket and take out a huge container of purple liquid and chug it"
				)
				HealthAmount = random.randint(40, 60)
				myhp = HealthAmount + myhp
				time.sleep(2)
				print(f"you healed {HealthAmount} and now have {myhp} HP left.")
		time.sleep(1)
	
		print("Charizard is deciding...")
	
		time.sleep(2)
	
		if BossHp > 0:
			BossChoice = random.randint(1, 4)
	
			# heal
			if BossHp < 90 and BossChoice == 1:
				BossHeal = random.randint(10, 30)
				BossHp = BossHp + BossHeal
				print(f"Charizard has healed {BossHeal} HP and now has {BossHp}.")
			else:
				BossDamage = random.randint(10, 40)
				myhp = myhp - BossDamage
				print(
					f"charizard has hit you and took away {BossDamage}, you now have {myhp} HP left"
				)
		if BossHp <= 0:
			win = input(
				"you have defeated the charizard, would u like to try again? Y/N"
			).lower()
			if win == "y":
				print("very well...")
				time.sleep(1)
				BossHp = 135
				myhp = 100
				print("Charizard has now healed back to 135 HP!")
			elif win == "n":
				print("ok")
				break
		if myhp <= 0:
			loss = input("you lost, would you like to try again? Y/N ").lower()
	
			# retry
			if loss == "y":
				print("travelling back in time...")
				time.sleep(1)
				continue
	
			# loss
			elif loss == "n":
				print("ok")
	
				bossfight()
				break
