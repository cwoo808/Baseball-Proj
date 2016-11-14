# Baseball-Proj
import numpy

class baseballgame:
	def __init__(self):
		self.innings = 9
		self.hometeamscore = 0
		self.awayteamscore = 0
	
	def at_bat(self):
		bat = numpy.random.choice(numpy.arange(1, 6), p=[0.10, 0.05, 0.03, 0.01, 0.81])
		# 1 = single(10%), 2 = double(5%), 3 = triple(3%), 4 = homerun(1%), 5 = strike(81%)
		if bat == 1:
			return 1
		elif bat == 2:
			return 2
		elif bat == 3:
			return 3
		elif bat == 4:
			return 4
		else:
			return 0
	
	def advance_runner(self):
		bases = []
		runs = 0
		strikes = 0
		outs = 0
		while outs < 3:
			while strikes < 3:
				at_bat = self.at_bat()
				if at_bat > 0:
					i = 0
					while i < len(bases):
						if bases[i] + at_bat >= 4:
							runs += 1
							bases.pop(i)
						else:
							bases[i] += at_bat
							i += 1
					bases.append(at_bat)
					strikes = 0
				else:
					strikes += 1
			if strikes == 3:
				strikes = 0
				outs += 1
		if outs == 3:
			return runs
			outs = 0
			bases = []
			runs = 0
	
	def inning(self):
		HT_batting = self.advance_runner()
		self.hometeamscore += HT_batting
		AT_batting = self.advance_runner()
		self.awayteamscore += AT_batting
	
	def game(self):
		first_inning = self.inning()
		print "1st Inning: Hometeam -", self.hometeamscore, "Awayteam -", self.awayteamscore
		second_inning = self.inning()
		print "2nd Inning: Hometeam -", self.hometeamscore, "Awayteam -", self.awayteamscore
		third_inning = self.inning()
		print "3rd Inning: Hometeam -", self.hometeamscore, "Awayteam -", self.awayteamscore
		fourth_inning = self.inning()
		print "4th Inning: Hometeam -", self.hometeamscore, "Awayteam -", self.awayteamscore
		fifth_inning = self.inning()
		print "5th Inning: Hometeam -", self.hometeamscore, "Awayteam -", self.awayteamscore
		sixth_inning = self.inning()
		print "6th Inning: Hometeam -", self.hometeamscore, "Awayteam -", self.awayteamscore
		seventh_inning = self.inning()
		print "7th Inning: Hometeam -", self.hometeamscore, "Awayteam -", self.awayteamscore
		eighth_inning = self.inning()
		print "8th Inning: Hometeam -", self.hometeamscore, "Awayteam -", self.awayteamscore
		ninth_inning = self.inning()
		print "9th Inning: Hometeam -", self.hometeamscore, "Awayteam -", self.awayteamscore
		if self.hometeamscore > self.awayteamscore:
			print "Hometeam Wins!"
		else:
			print "Awayteam Wins!"

my_game = baseballgame()
my_game.game()





