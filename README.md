<h1>Analyzing Music Events in LA</h1>
<h2>Project Objective</h2>
<h4><em>What problem are you solving</em></h4>
<p>Los Angeles is among the top cities Ticketmaster provides tickets for. It needs to be more clear as to which venues host the most shows and which genres are commonly performed at those venues as well as if the venue has an impact on ticket prices. To gain a better understanding, I will be analyzing 200 music events in Los Angeles and determine trends and patterns in venue popularity and price ranges.</p>

<h4><em>How are you solving this problem?</em></h4>
<p>I will solve this problem by using Ticketmaster’s API to retrieve the 200 music events in LA. I will use their API to get the artist's name, genre, subgenre, event date, venue, venue address, and minimum and maximum price. I will then explore the data to identify popular venues and genres and determine whether there is a correlation between prices and venue popularity. These insights can provide valuable information for stakeholders, such as event organizers, entertainment companies, venue owners, and artists, to make decisions and improve their event planning. </p>

<h2>Job Description</h2>
<p>Ticketmaster, being the largest ticket services provider in the US, offers tickets for various events such as theater performances, sports events, concerts, and many more. They are looking for a Data Analyst to join their Insights and Analytics Team. As a Data Analyst, some of the responsibilities include handling large data sets to provide venue/client analyses and customer lifetime value, analyzing and translating data in order to provide actionable insights that help determine revenue opportunities, and collaborating with business stakeholders to understand their needs. </p>

<p>This project is related to the job posting as it uses event data to provide insights and help decision-making for event planning and revenue opportunities. The project involves retrieving data using Ticketmaster’s API and then analyzing it to identify popular genres and venues and analyzing the correlation between prices and venue popularity. These insights can help stakeholders with their event planning and increase their revenue. </p>

<h2>Data</h2>
<h6><em>Ticketmaster API I used to retrieve the data:</em></h6>
https://developer.ticketmaster.com/products-and-docs/apis/discovery-api/v2/

<p>I created four tables in my Ticketmaster database called shows, information, upcoming_events, and price.</p>
<p>Shows Table:
CREATE TABLE shows (
	artist_id INT NOT NULL AUTO_INCREMENT,
	show_name VARCHAR(255) NOT NULL,
	genre VARCHAR(30) NOT NULL,
	subgenre VARCHAR(255),
	PRIMARY KEY(artist_id)
);

Information Table:
CREATE TABLE information(
	event_id VARCHAR(255) NOT NULL,
	artist_id INT NOT NULL AUTO_INCREMENT,
	show_name VARCHAR(255) NOT NULL,
	event_date DATE NOT NULL,
	venue VARCHAR(255) NOT NULL,
	address VARCHAR(255) NOT NULL,
	city VARCHAR (255) NOT NULL,
	state_code VARCHAR (255) NOT NULL,
	ticket_limit INT(5) NOT NULL,
	PRIMARY KEY(event_id),
	FOREIGN KEY (artist_id) REFERENCES shows(artist_id)
);

Upcoming_events Table:
CREATE TABLE upcoming_events(
	artist_id INT NOT NULL AUTO_INCREMENT,
	show_name VARCHAR(255) NOT NULL,
	total INT(5) NOT NULL,
	ticketmaster INT(5) NOT NULL,
	PRIMARY KEY(artist_id),
	FOREIGN KEY (artist_id) REFERENCES shows(artist_id)
);

Price Table:
CREATE TABLE price(
	event_id VARCHAR(255) NOT NULL,
	artist_id INT NOT NULL AUTO_INCREMENT,
	show_name VARCHAR(255) NOT NULL,
	min_price FLOAT NOT NULL,
	max_price FLOAT NOT NULL,
	PRIMARY KEY (event_id),
	FOREIGN KEY (artist_id) REFERENCES shows(artist_id)
);
</p>

<h4>Notebooks</h4>
