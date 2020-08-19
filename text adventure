import sys
import random


# character stats
class Character:
    def __init__(self, name, lvl, maxhp, hp, power, accuracy, exp, flee):
        self.name = name
        self.lvl = lvl
        self.maxhp = maxhp
        self.hp = hp
        self.power = power
        self.accuracy = accuracy
        self.exp = exp
        self.flee = flee


# weapon stats and types
class Weapon:
    def __init__(self, name, power, accuracy):
        self.name = name
        self.power = power
        self.accuracy = accuracy


bs = Weapon('Basic Sword', 30, .90)
bl = Weapon('Basic Lance', 40, .80)
ba = Weapon('Basic Axe', 50, .70)

ins = Weapon('Intermediate Sword', 40, .80)
inl = Weapon('Intermediate Lance', 50, .70)
ina = Weapon('Intermediate Axe', 60, .60)

ads = Weapon('Advanced Sword', 50, .70)
adl = Weapon('Advanced Lance', 60, .60)
ada = Weapon('Advanced Axe', 70, .50)


# enemy stats and types
class Enemy:
    def __init__(self, name, hp, power, accuracy, exp, flee):
        self.name = name
        self.hp = hp
        self.power = power
        self.accuracy = accuracy
        self.exp = exp
        self.flee = flee


ogre1 = Enemy('Ogre', 100, 10, .75, 40, .50)
ogre2 = Enemy('Ogre', 100, 10, .75, 40, .50)
ogre3 = Enemy('Ogre', 100, 10, .75, 40, .50)

mushroom1 = Enemy('Giant Mushroom', 100, 15, .65, 40, .50)
mushroom2 = Enemy('Giant Mushroom', 100, 15, .65, 40, .50)
mushroom3 = Enemy('Giant Mushroom', 100, 15, .65, 40, .50)

scorpion1 = Enemy('Fire Scorpion', 120, 20, .75, 60, .60)
scorpion2 = Enemy('Fire Scorpion', 120, 20, .75, 60, .60)
scorpion3 = Enemy('Fire Scorpion', 120, 20, .75, 60, .60)

pixie1 = Enemy('Corrupted Pixie', 130, 25, .65, 60, .60)
pixie2 = Enemy('Corrupted Pixie', 130, 25, .65, 60, .60)
pixie3 = Enemy('Corrupted Pixie', 130, 25, .65, 60, .60)

dknight = Enemy('Dark Knight', 150, 30, .80, 80, .50)
dknight = Enemy('Dark Knight', 150, 30, .80, 80, .50)

dking = Enemy('Dragon King Fellheart', 200, 35, .6, 100, 1.00)


# food stats and types
class Food:
    def __init__(self, name, recovery):
        self.name = name
        self.recovery = recovery

    def inspect(self):
        print('Name: {0}, Recovery: {1}'.format(self.name, self.recovery))


apple = Food('apple', 20)
meat = Food('meat', 30)
potion = Food('potion', 50)
greaterpotion = Food('greater potion', 80)
elixer = Food('elixer', 10000)


def ItemGet(item):
    return 'You have picked up {0}'.format(item)


# inventory logistics
weaponinventory = []
foodinventory = []
winventory = {}
finventory = {}
inv = ', '


# combat functions
def fleecheck(enemy):
    if random.uniform(0,enemy.flee) <= player.flee:
        return True
    else:
        return False


def damage(weapon, unit, target):
    if weapon == None:
        totaldamage = unit.power
    else:
        totaldamage = weapon.power + unit.power
    target.hp = target.hp - totaldamage
    if target.hp <= 0:
        print('{0} has fallen'.format(target.name))
        if target.name == player.name:
            print('Game Over!')
            sys.exit('Exiting Game...')
    else:
        print('{0} has {1} hp left!'.format(target.name, target.hp))


def hitcheck(weapon, unit, target):
    if weapon == None:
        totalhit = unit.accuracy
    else:
        totalhit = unit.accuracy + weapon.accuracy
    if random.random() <= totalhit:
        print('Hit!')
        damage(weapon, unit, target)
    else:
        print('Miss!')


def recover(food):
    player.hp = min(player.maxhp, food.recovery + player.hp)
    print('Your HP is now {0}'.format(player.hp))


def experience(enemy):
    print('You have gained {0} experience points.'.format(enemy.exp))
    player.exp += enemy.exp
    if player.exp >= 100:
        player.lvl += 1
        player.maxhp += 20
        player.power += 10
        player.accuracy += .10
        player.hp = player.maxhp
        player.exp = player.exp - 100
        print('Congratulations! You have leveled up!')
        print('Stats -  HP: {0}, Power: {1}, Accuracy{2}: '.format(player.maxhp, player.power, player.accuracy))


# game start
answer = input('Start? (yes/no): ').lower().strip()

if answer == 'yes':
    print('Welcome to Novis...'
          'This is a land that is ruled by the Dragon King Fellheart...'
          'It is up to you to stand up to his tyranny.')
    playername = input('Please tell me your name, hero... ')
    print('We wish you luck on your quest {0}'.format(playername))
    player = Character(playername, 1, 100, 100, 20, .10, 0, .50)
    print('This will be a long journey, choose your weapon wisely.')
    input('Press Enter to Continue')
    print(
        'Swords have low power but high accuracy. '
        'Lances have medium power and accuracy. '
        'Axes have high power but low accuracy.')
    input('Press Enter to Continue')
    currentequip = input('Choose your weapon (Basic Sword, Basic Lance, Basic Axe): ')
    print(ItemGet(currentequip))
    if currentequip == 'basic sword':
        weaponinventory.append(bs.name)
        winventory.update({'basic sword': bs})
    elif currentequip == 'basic lance':
        weaponinventory.append(bl.name)
        winventory.update({'basic lance': bl})
    else:
        weaponinventory.append(ba.name)
        winventory.update({'basic axe': ba})

    print('You must first travel to the Dragon King\'s Lair')
    answer = input('Will you travel through the Dark Swamp, or the Deep Gorge?: ').lower().strip()
    # dark swamp route
    if answer == 'dark swamp':
        print('Very well, good luck {0}'.format(playername))
        print('You travel to the Dark Swamp. '
              'The swamp is dank and depressing. '
              'You feel your feet sink into the ooze.')
        answer = input(
            'You find an apple. A bit odd to find in a swamp no? Inspect the apple? (yes/no): ').lower().strip()
        if answer == 'yes':
            apple.inspect()
        answer = input('Do you take the apple? (yes/no): ').lower().strip()
        if answer == 'yes':
            foodinventory.append(apple.name)
            finventory.update({'apple': apple})
        else:
            pass
        print('You travel deep into the swamp.')
        answer = input('You encounter an Ogre, this must be his swamp. Attempt to flee? (yes/no): ').lower().strip()
        if answer == 'yes':
            if not fleecheck(ogre1):
                print('You have failed to flee! Prepare for battle!')
                while ogre1.hp > 0:
                    answer = input('What will you do? (Fight, Use Item): ').lower().strip()
                    if answer == 'fight':
                        answer = input('Choose your weapon: {0} '.format(weaponinventory)).lower().strip()
                        hitcheck(winventory[answer], player, ogre1)
                        if ogre1.hp <= 0:
                            break
                        print('The ogre attacks!')
                        hitcheck(None, ogre1, player)
                    else:
                        answer = input('Choose which item to use: {0} '.format(foodinventory)).lower().strip()
                        recover(finventory[answer])
                print('You have defeated Ogre')
                experience(ogre1)

            else:
                print('You have fled successfully!')
        else:
            print('Prepare for battle!')
            while ogre1.hp > 0:
                answer = input('What will you do? (Fight, Use Item): ').lower().strip()
                if answer == 'fight':
                    answer = input('Choose your weapon: {0} '.format(weaponinventory)).lower().strip()
                    hitcheck(winventory[answer], player, ogre1)
                    if ogre1.hp <= 0:
                        break
                    print('The ogre attacks!')
                    hitcheck(None, ogre1, player)
                else:
                    answer = input('Choose which item to use: {0} '.format(foodinventory)).lower().strip()
                    recover(finventory[answer])
            print('You have defeated Ogre')
            experience(ogre1)

    # deep gorge route
    elif answer == 'deep gorge':
        print('Very well, good luck {0}'.format(playername))
        print('You travel to the Deep Gorge. '
              'The walls surround you on both sides, making you feel cramped. '
              'Your footsteps echo into the distance.')
        answer = input('You find an apple, but no apple tree? Inspect the apple? (yes/no): ').lower().strip()
        if answer == 'yes':
            apple.inspect()
        answer = input('Do you take the apple? (yes/no): ').lower().strip()
        if answer == 'yes':
            foodinventory.append(apple.name)
            finventory.update({'apple': apple})
        else:
            pass
        print('You travel deep into the gorge.')
        answer = input(
            'You encounter a Giant Mushroom; it is quite grotesque. Attempt to flee? (yes/no): ').lower().strip()
        if answer == 'yes':
            if not fleecheck(mushroom1):
                print('You have failed to flee! Prepare for battle!')
                while ogre1.hp > 0:
                    answer = input('What will you do? (Fight, Use Item): ').lower().strip()
                    if answer == 'fight':
                        answer = input('Choose your weapon: {0} '.format(weaponinventory)).lower().strip()
                        hitcheck(winventory[answer], player, mushroom1)
                        if mushroom1.hp <= 0:
                            break
                        print('The giant mushroom attacks!')
                        hitcheck(None, mushroom1, player)
                    else:
                        answer = input('Choose which item to use: {0} '.format(foodinventory)).lower().strip()
                        recover(finventory[answer])
                print('You have defeated Giant Mushroom')
                experience(mushroom1)

            else:
                print('You have fled successfully!')
        else:
            print('Prepare for battle!')
            while mushroom1.hp > 0:
                answer = input('What will you do? (Fight, Use Item): ').lower().strip()
                if answer == 'fight':
                    answer = input('Choose your weapon: {0} '.format(weaponinventory)).lower().strip()
                    hitcheck(winventory[answer], player, mushroom1)
                    if mushroom1.hp <= 0:
                        break
                    print('The giant mushroom attacks!')
                    hitcheck(None, mushroom1, player)
                else:
                    answer = input('Choose which item to use: {0} '.format(foodinventory)).lower().strip()
                    recover(finventory[answer])
            print('You have defeated Giant Mushroom')
            experience(mushroom1)
    else:
        print("That is not a valid answer, the Dragon King/'s reign continues.")





else:
    print('Maybe another time!')
