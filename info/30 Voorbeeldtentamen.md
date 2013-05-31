# Voorbeeldtentamen

Je moet werkende code aanleveren die het juiste antwoord geeft. Kopieer voor elke opgave de voorbeeldcode en werk daarin je antwoord uit. Lever alle code in 1 bestand in. Als je dit goed doet krijg je van alle opgaven het antwoord te zien zodra je het programma start.

Je hebt 1 uur de tijd voor dit tentamen.

### opgave a

Gegeven een `lijst` van hele getallen, bereken en retourneer het gemiddelde van alle waarden deelbaar door `deler`. Dit is niet per se wiskundig zinvol. Maak gebruik van een `for`-loop.

	# opgave a
	# gemiddelde van deelbare getallen 1-1000
	
	def gemiddelde_deelbare(lijst, deler):
		# TODO

	# test de functie gemiddelde_deelbare
	getallen = []
	for i in range(1, 1001):
		getallen.append(i)
	print "opgave a:"
	print gemiddelde_deelbare(getallen, 7)

### opgave b

Gegeven de lijst `M`, gebruik for-loops om de volgende tekst uit te printen:

	It is a European swallow
	It is a European coconut
	It is a African swallow
	It is a African coconut

Gebruik deze code als basis:

	# opgave b
	# vogels en steenvruchten

	# test de functie permute_and_print
	print "opgave b:"
	M = [['European', 'African'], ['swallow', 'coconut']]
	permute_and_print(M)


