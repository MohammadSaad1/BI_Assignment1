# BI_Assignment1

# 1

Pricelist.csv, pricelist.txt, price_average.txt and prices.png

# 2

2)	Just a regular text file and a regular CSV file, and  price_average.txt which contains the price average. It also contains a png file with a diagram of plots.

# 3

3307228.119047619
# 4
First function:
def download_txt(url, save_path='./downloaded'):
	    response = requests.get(url)
	    with open(save_path, 'wb') as f:
	        f.write(response.content)
What it does is go to the given link and gets the text file that it leads to, and then afterwards writes it out into a separate document in the local storage.

Second function

def generate_csv(txt_input_path, csv_output_path):
	    with open(txt_input_path, encoding='utf-8') as f:
	        txt_content = f.readlines()
	

	    rows = [['street', 'city', 'price', 'sqm', 'price_per_sqm']]
	    for line in txt_content:
	        line = line.rstrip().replace('  * ', '')
	        address, price, sqm = line.split('\t')
	        street, city = address.split('; ')
	        price_per_sqm = int(price) // int(sqm)
	        row = (street, city, price, sqm, price_per_sqm)
	        rows.append(row)
if platform.system() == 'Windows':
	        newline=''
	    else:
	        newline=None
	

	    with open(csv_output_path, 'w', newline=newline, encoding='utf-8') as f:
	        output_writer = csv.writer(f)
	        for row in rows:
	            output_writer.writerow(row)

	
Denne kode åbner først den allerede importerede tekst fil hvorefter den åbner den, og så læser den. Derefter defineres row strukturen, hvorefter man for hver linje i dokumentet splitter dataen så den passer i overensstemmelse med de headers som er givet.  Derefter tilføjer man den givne row ind i listen af rows.

Derefter tjekker man for hvilket styresystem man er på i øjeblikket hvor man derefter i en condition siger at new_line skal være ”” hvis windows og null hvis andet.
Derefter skriver man den liste man har af rows ud i en CSV fil.


ef read_prices(csv_input_path):
	    with open(csv_input_path, encoding='utf-8') as f:
	        reader = csv.reader(f)
	        _ = next(reader)
	

	        idxs = []
	        prices = []
	        for row in reader:
	            _, _, price, _, _ = row
	            idxs.append(reader.line_num)
	            prices.append(int(price))
	

	    return list(zip(idxs, prices))

I denne function gør man blot det at man åbner den csv fil man nu har og indlæser den, hvorefter man gennemgår hver row og tilføjer nummeret på row i en liste, og dens pris i en anden liste.

def compute_avg_price(data):
	    _, prices = zip(*data)
	    avg_price = statistics.mean(prices)
	

	    with open('/tmp/avg_price.txt', 'w', encoding='utf-8') as f:
	        f.write(str(avg_price))
	

	    return avg_price

Denne funktion bruges til at udregne average price. Her regner man average price og derefter tilføjet den i avg_price.txt.

Herefter kører man alt denne funktionalitet i det der svarer til en ”main” metode, hvor han henter txt filen fra hjemmesiden og så bruger de resterende metoder. 


# 5

![alt text](https://imgur.com/IIWCROL)


