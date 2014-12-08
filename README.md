kmessaging
==========

Class implement a private messaging system that stores messages in a MySQL database.
It can be used to exchange private messages between users of a site.

The class provides means to:

- Send a message
- Get the title, body, sender and receiver a of a message
- Mark a message as read
- Retrieve all message from or to a given user
- Delete a message

Needed requirements:
==========
Create a Mysql table with the following code

	CREATE TABLE `msgtbl` (
	  `idMsg` int(11) NOT NULL auto_increment,
	  `title` varchar(255) NOT NULL default '',
	  `body` text NOT NULL,
	  `sender` int(11) NOT NULL default '0',
	  `receiver` int(11) NOT NULL default '0',
	  `senderLevel` int(11) NOT NULL default '0',
	  `readed` int(11) NOT NULL default '0',
	  `date` timestamp NOT NULL default CURRENT_TIMESTAMP on update CURRENT_TIMESTAMP,
	  PRIMARY KEY  (`idMsg`)
	);

Code example
==========
	
	$message = new KMessaging(true);
	$message->SendMessege('Promotion','Today we have a brand new promotion from the pack number5',10,30,3);//user 10 sends a message to user 30 and have a level of 3
	$array = $message->GetAllMesseges(0,30);