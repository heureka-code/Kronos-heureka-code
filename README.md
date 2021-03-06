#Kronos – Datums- und Uhrzeitangaben
___

##Exceptions

* __KronosException__ &rarr; abgeleitet von Exception. 
  Basisklasse aller Exceptions des Kronosprojekts
  
###Exceptionhierarchie

* KronosException
    * ZeitException
        * DatumException
            * JahrException
                * JahrKeineGanzeZahl
            * MonatsException
                * KeineGueltigeMonatsposition
                * KeinGueltigerMonatscode
                * KeineGueltigeTageszahl
                * KeinGueltigerMonatsname
            * TagException
                * TagKeineGanzeZahl
                * TagKleinerAlsEins
                * TagZuGross
            * WochentagException
                * UngueltigerWochentagname
                * UngueltigeWochentagposition
        * UhrzeitException
            * StundeException
                * StundeKeineGanzeZahl
                * StundeZuGross
                * StundeZuKlein
            * MinuteException
                * MinuteKeineGanzeZahl
                * MinuteZuGross
                * MinuteZuKlein
            * SekundeException
                * SekundeKeineGanzeZahl
                * SekundeZuGross
                * SekundeZuKlein
___
##Notationen

###Exceptions

###Datum

Die Datumsnotationen werden unterteilt in:

* __DatumsNotationNonSplitted__ &rarr; Die Datumsnotationen ohne Trennzeichen bezeichnet
    * __TTMMJJJJ__ &rarr; Tag (2 Stellen) Monat (2 Stellen) Jahr (4 Stellen) 
      * __TTMMJJJJ_NON_SPLITTED__
    * __JJJJMMTT__
      * __JJJJMMTT_NON_SPLITTED__ &rarr; Jahr (4 Stellen) Monat (2 Stellen) Tag (2 Stellen)
    
* __DatumsNotationSplitted__ &rarr; Die Datumsnotationen mit Trennzeichen bezeichnet
    * __TMJ__ &rarr; Datumsnotations-Unterklasse für eine Folge von __Tag__ _[Trennzeichen]_ __Monat__ _[Trennzeichen]_ __Jahr__
      
      |    Instanz    |   Trenner   |
      | :------------ | :---------: |
      | __TMJ_DOT__   | _Punkt_ (.) |
      | __TMJ_DASH__  | _Minus_ (-) |
      | __TMJ_SLASH__ | _Slash_ (/) |
    * __JMT__ &rarr; Datumsnotations-Unterklasse für eine Folge von __Jahr__ _[Trennzeichen]_ __Monat__ _[Trennzeichen]_ __Tag__
        
      |    Instanz    |   Trenner   |
      | :------------ | :---------: |
      | __JMT_DOT__   | _Punkt_ (.) |
      | __JMT_DASH__  | _Minus_ (-) |
      | __JMT_SLASH__ | _Slash_ (/) |
    
### <span name="NotationUhrzeit">Uhrzeit</span>

Die Uhrzeitnotationen werden unterteilt in:

* __UhrzeitNotationNonSplitted__ &rarr; Die Uhrzeitnotationen ohne Trennzeichen bezeichnet
    * __HHMMSS__
      * __HHMMSS_NON_SPLITTED__
    * __SSMMHH__
      * __SSMMHH_NON_SPLITTED__

* __UhrzeitNotationSplitted__ &rarr; Die Uhrzeitnotationen mit Trennzeichen bezeichnet
    * __HMS__ &rarr; Uhrzeiznotations-Unterklasse für eine Folge von __Stunde__ _[Trennzeichen]_ __Minute__ _[Trennzeichen]_ __Sekunde__
    
      |    Instanz    |      Trenner      |
      | :------------ | :---------------: |
      | __HMS_DOT__   | _Punkt_ (.)       |
      | __HMS_DASH__  | _Minus_ (-)       |
      | __HMS_SLASH__ | _Slash_ (/)       |
      | __HMS_COLON__ | _Doppelpunkt_ (:) |
    * __SMH__ &rarr; Uhrzeiznotations-Unterklasse für eine Folge von __Sekunde__ _[Trennzeichen]_ __Minute__ _[Trennzeichen]_ __Stunde__
      
      |    Instanz    |      Trenner      |
      | :------------ | :---------------: |
      | __SMH_DOT__   | _Punkt_ (.)       |
      | __SMH_DASH__  | _Minus_ (-)       |
      | __SMH_SLASH__ | _Slash_ (/)       |
      | __SMH_COLON__ | _Doppelpunkt_ (:) |
___

##Datum

###Exceptions

* __DatumException__ &rarr; abgeleitet von __ZeitException__

###Methoden

```__init__```: Nimmt, den Tag, den Monat und das Jahr als int-Werte.

```__repr__```: Gibt den Representations-String des Datums zurück.

```ist_schaltjahr```: Statische Methode, die prüft, ob ein bestimmtes Jahr ein Schaltjahr ist.

```tag```: Liefert den Tag des Datums.

```monat```: Liefert den Monat des Datums.

```jahr```: Liefert das Jahr des Datums.

```wochentag```: Property-Attribut, das den Wochentag des Datums liefert.

```monatscode```: Property-Attribut, das den Monatscode zur Wochentagsberechnung liefert.

```jahrescode```: Property-Attribut, das den Jahrescode zur Wochentagsberechnung liefert.

```von_datums_notation```: Errechnet ein Datum aus einem String einer gewissen Notation.

```__eq__```: Prüft, ob ein Datum einem anderen gleicht.

```__ne__```: Gibt das invertierte Ergebnis der Methode ```__eq__``` zurück.

```__lt__```: Prüft, ob ein Datum kleiner oder gleich dem Argument ist.

```__gt__```: Prüft, ob ein Datum größer oder gleich dem Argument ist.

```__le__```: Prüft, ob das Datum kleiner oder gleich dem Argument ist.

```__ge__```: Prüft, ob das Datum größer oder gleich dem Argument ist.

###Tag

Die Klasse zum Speichern eines Tages

####Exceptions

* __TagException__ &rarr; abgeleitet von __DatumException__. Basisklasse aller Exceptions, die den Tag betreffen.
* __TagKeineGanzeZahl__ &rarr; abgeleitet von __TagException__. Wird ausgelöst, 
  wenn der gegebene Tag keine ganze Zahl also ein float-Wert, 
  oder ein nicht zur Ganzzahl konvertierbarer Typ ist, wie ein String, der nicht nur aus Zahlen besteht.
* __TagKleinerAlsEins__ &rarr; abgeleitet von __TagException__. Wird ausgelöst, 
  wenn ein gegebener Tag kleiner als 0, also unmöglich ein gültiger Tag ist.
* __TagZuGross__ &rarr; abgeleitet von __TagException__. Wird ausgelöst, 
  wenn ein gegebener Tag zu groß für einen Monat und somit ungültig ist.

####Methoden

```__init__```: Nimmt im Konstruktor den Tag als ganze Zahl.

```tag```: Property-Attribut zum Abrufen und bedingtem Setzen vom Tag.

```monats_pruefung```: Methode um zu prüfen, ob die Tagesanzahl für einen gegebenen Monat zu groß ist.

```__repr__```: Ein Representations-String für den Tag.

```__str__```: Liefert einen String der Tageszahl ohne zusätzlichen Text

```__int__```: Die Tageszahl als Integer.

```__eq__```: Prüft, ob der Tag gleich dem Argument ist. 
Hierbei wird der Integerwert des Arguments verwendet, 
weshalb auch ein String, eine Tag-Instanz oder ähnliches gegeben werden können.

```__ne__```: Prüft, ob der Tag ungleich dem Argument ist. 
Hierzu wird der Wert der Methode ```__eq__``` invertiert, weshalb auch dafür passende Werte gegeben werden können.

```__lt__```: Prüft, ob der Wert des Tages kleiner ist, als der int-Wert des Arguments.

```__gt__```: Prüft, ob der Wert des Tages größer ist, als der int-Wert des Arguments.

```__le__```: Prüft auf Basis der Methoden ```__lt__``` und ```__eq__```, 
ob der Wert des Tages kleiner oder gleich dem int-Wert des Arguments ist.

```__ge__```: Prüft auf Basis der Methoden ```__gt__``` und ```__eq__```,
ob der Wert des Tages größer oder gleich dem int-Wert des Arguments ist.

###Monat

Die Klasse zum Speichern eines Monats

####Vordefinierte Monate

|   Konstante   |    Name     | Position | Monatscode |  Anzahl Tage  | Anzahl Tage im Schaltjahr |
| :------------ | :---------- | -------: | ---------: | ------------: | ------------------------: |
| __JANUAR__    | _Januar_    |      1   | 6          | 31            | 31                        |
| __FEBRUAR__   | _Februar_   |      2   | 2          | 28            | _29_                      |
| __MAERZ__     | _März_      |      3   | 2          | 31            | 31                        |
| __APRIL__     | _April_     |      4   | 5          | 30            | 30                        |
| __MAI__       | _Mai_       |      5   | 0          | 31            | 31                        |
| __JUNI__      | _Juni_      |      6   | 3          | 30            | 30                        |
| __JULI__      | _Juli_      |      7   | 5          | 31            | 31                        |
| __AUGUST__    | _August_    |      8   | 1          | 31            | 31                        |
| __SEPTEMBER__ | _September_ |      9   | 4          | 30            | 30                        |
| __OKTOBER__   | _Oktober_   |     10   | 6          | 31            | 31                        |
| __NOVEMBER__  | _November_  |     11   | 2          | 30            | 30                        |
| __DEZEMBER__  | _Dezember_  |     12   | 4          | 31            | 31                        |

####Exceptions

* __MonatsException__ &rarr; abgeleitet von __DatumException__. Basisklasse aller Exceptions, die den Monat betreffen.
* __KeinGueltigerMonatscode__ &rarr; abgeleitet von __MonatsException__. Wird ausgelöst, 
  wenn ein für die Wochentagsberechnung ungültiger Monatscode verwendet wurde.
* __KeineGueltigeMonatsposition__ &rarr; abgeleitet von __MonatsException__. Wird ausgelöst, 
  wenn eine ungültige Monatsposition – z.B. erster, zweiter, dritter, etc. – gegeben wird
* __KeineGueltigeTageszahl__ &rarr; abgeleitet von __MonatsException__. Wird ausgelöst, 
  wenn eine für den Monat ungüeltige Anzahl Tage gegeben wurde.
* __KeinGueltigerMonatsname__ &rarr; abgeleitet von __MonatsException__. Wird ausgelöst, 
  wenn ein ungültiger Name für einen Monat vergeben wurde.
  
####Methoden der Monat-Klasse

```__init__```: Nimmt einen Namen, eine Monatsposition, 
einen Monatscode, eine Anzahl Tage, die der Monat im normalen Jahr hat, 
eine optionale Tagesanzahl für ein eventuell abweichendes Schaltjahr.

```__copy__```: Liefert eine Kopie des Monats.

```__repr__```: Gibt einen Representations-String des Monats zurück.

```__str__```: Gibt den Namen des Monats zurück.

```__int__```: Gibt die Position des jeweiligen Monats im Jahr als Integer zurück.

```name```: Property-Attribut, das den Namen des Monats in einer __Monatsname__-Instanz liefert.

```position```: Property-Attribut, das die Position des Monats im Jahr in einer __Monatsposition__-Instanz liefert.

```monatscode```: Property-Attribut, das den Monatscode für die Wochentagsberechnung liefert.

```anzahl_tage```: Property-Attribut, 
das die Anzahl Tage in einem normalen Jahr in einer __AnzahlTageImMonat__-Instanz liefert.

```anzahl_tage_im_schaltjahr```: Property-Attribut, 
das die Anzahl Tage in einem Schaltjahr in einer __AnzahlTageImMonat__-Instanz liefert.

####Methoden der AnzahlTageImMonat-Klasse

```__init__```: Nimmt die Anzahl Tage als int-Wert.

```anzahl_tage```: Property-Attribut, das die Anzahl an Tagen als Integer liefert.

```__int__```: Liefert die Anzahl an Tagen als int-Wert.

```__repr__```: Liefert einen Representations-String für die Tageszahl.

```__str__```: Liefert die Anzahl an Tagen als String ohne zusätzliche Zeichen.

```__eq__```: Prüft, ob der Wert der Tageszahl dem Argument entspricht.

```__ne__```: Liefert den invertierten Wert der Methode ```__eq__```.

####Methoden der Monatscode-Klasse

```__init__```: Nimmt den Monatscode als int-Wert oder eine Instanz der __Monatscode__-Klasse.

```monatscode```: Property-Attribut, das den Monatscode als int-Wert liefert.

```__int__```: Liefert den Monatscode als int-Wert.

```__repr__```: Liefert einen Representations-String für das Objekt.

####Methoden der Monatsname-Klasse

```__init__```: Nimmt den Monatsnamen als String oder eine Instanz der Klasse __Monatsname__.

```monatsname```: Property-Attribut, das den Monatsnamen liefert.

```__repr__```: Liefert einen Representations-String für das Objekt.

```__str__```: Liefert den Monatsnamen als String ohne zusätzliche Zeichen.

####Methoden der Monatsposition-Klasse

```__init__```: Nimmt die Position des Monats im Jahr als int-Wert oder Instanz der __Monatsposition__-Klasse.

```position```: Property-Attribut, das die Position als int-Wert liefert.

```__int__```: Liefert die Monatsposition als Integer.

```__repr__```: Liefert den Representations-String für das Objekt.


###Jahr

Die Klasse zum Speichern eines Jahres.
####Exceptions

* __JahrException__ &rarr; abgeleitet von __DatumException__. 
  Ist die Basisklasse der Exceptions, die mit dem Jahr zusammenhängen.
* __JahrKeineGanzeZahl__ &rarr; abgeleitet von __JahrException__. 
  Wird ausgelöst, wenn das gegebene Jahr keine ganze Zahl ist.

####Methoden der Jahr-Klasse

```__init__```: Nimmt das Jahr und die Zeitrechnung, die standardmäßig der allgemeinen Zeitrechnung entspricht.

```jahr```: Property-Attribut, das das Jahr als int-Wert liefert.

```zeitrechnung```: Property-Attribut, das die Zeitrechnung liefert.

```__int__```: Liefert den int-Wert des Jahres ohne Zeitrechnungsinformation.

```__repr__```: Liefert den Representations-String des Objekts.

###Zeitrechnung

####Vordefinierte Zeitrechnungen

| Konstante     | Name                        | Kürzel    | Differenz zur allgemeinen Zeitrechnung |
| :------------ | :-------------------------- | :-------- | -------------------------------------: |
| __A_U_C__     | _Ab urbem condita_          | A.u.c.    | 753                                    |
| __A_Z__       | _Allgemeine Zeitrechnung_   | A.Z.      | 0                                      |

####Methoden
```__init__```: Nimmt den Namen, das Kürzel und die Entfernung zur Allgemeinen Zeitrechnung.

```convert```: Konvertiert ein Jahr von dieser in eine andere Zeitrechnung.

```delta```: Property-Attribut, das die Differenz zur Allgemeinen Zeitrechnung liefert.

```name```: Property-Attribut, das den Namen der Zeitrechnung liefert.

```kuerzel```: Property-Attribut, das das Kürzel der Zeitrechnung liefert.

```__repr__```: Liefert den Representations-String des Objekts.

###Wochentag

Die Klasse zum Speichern eines Wochentages.

####Wochentage

#####Vordefinierte Wochentage

|     Konstante     |       Name       | Position |
| :---------------- | :--------------- | -------: |
| __SONNTAG__       | _Sonntag_        | 0        |
| __MONTAG__        | _Montag_         | 1        |
| __DIENSTAG__      | _Dienstag_       | 2        |
| __MITTWOCH__      | _Mittwoch_       | 3        |
| __DONNERSTAG__    | _Donnerstag_     | 4        |
| __FREITAG__       | _Freitag_        | 5        |
| __SAMSTAG__       | _Samstag_        | 6        |

#####Exceptions

* __WochentagException__ &rarr; abgeleitet von __DatumException__. Basisklasse aller Exceptions, 
  die mit dem Wochentag zusammenhängen.
* __UngueltigerWochentagname__ &rarr; abgeleitet von __WochentagException__. Wird ausgelöst, 
  wenn ein ungültiger Name für den Wochentag gegeben wurde
* __UngueltigeWochentagposition__ &rarr; abgeleitet von __WochentagException__. Wird ausgelöst, 
  wenn eine unmögliche Wochentagposition gegeben wurde.

#####Methoden der Wochentage-Klasse

```get```: Statische Methode, die den Wochentag einer gewissen Position zurückgibt.

```__getitem__```: Gibt den Wochentag einer gewissen Position zurück.

```__iter__```: Liefert einen Iterator, der durch die Wochentage läuft.

####Methoden der Klasse WochentageIterator

```position```: Property-Attribut, das die aktuelle Position des Iterators liefert.

```__next__```: Lässt den Iterator eins weiter zählen.

### Methoden der Wochentag-Klasse

```__init__```: Nimmt den Namen und die Position des Wochentags

```wochentag_name```: Property-Attribut, das den Namen des Wochentages liefert.

```wochentag_position```: Property-Attribut, das die Position des Wochentages liefert.

```__repr__```: Liefert einen Representations-String für das Objekt zurück.

```__int__```: Liefert die Position des Wochentages als int-Wert.

###Methoden der WochentagName-Klasse

```__init__```: Nimmt den Namen des Wochentags als String.

```wochentag_name```: Property-Attribut, das den Namen des Wochentags liefert.

```__repr__```: Liefert den Representations-String des Objekts.

```__str__```: Liefert den Namen des Wochentags als String ohne zusätzliche Zeichen.

```__eq__```: Prüft, ob der Name dem String-Wert des Arguments entspricht.

```__ne__```: Gibt das invertierte Ergebnis der Methode ```__eq__``` zurück.

###Methoden der WochentagPosition-Klasse

```__init__```: Nimt die Positon des Tages in der Woche als int-Wert.

```wochentag_position```: Property-Attribut, das die Position des Wochentags liefert.

```__int__```: Liefert die Position als int-Wert.

```__repr__```: Liefert den Representations-String des Objeks zurück.

```__eq__```: Gibt zurück, ob die Position dem int-Wert des Arguments entspricht.

```__ne__```: Gibt das invertierte Ergebnis der Methode ```__eq__``` zurück.

```__lt__```: Prüft, ob die Position kleiner als der int-Wert des Arguments ist.

```__gt__```: Prüft, ob die Position größer als der int-Wert des Arguments ist.

```__le__```: Prüft, ob die Position kleiner oder gleich dem int-Wert des Arguments ist.

```__ge__```: Prüft, ob die Position größer oder gleich dem int-Wert des Arguments ist.

___

##Uhrzeit

###Exceptions

* __UhrzeitException__ &rarr; Basisklasse für Exceptions, die mit der Uhrzeit zusammenhängen.

###Methoden

```__init__```: Nimmt eine Stunde, Minute und optional eine Sekunde als int-Werte. 

```von_uhrzeit_notation```: Interpretiert einen String einer bestimmten Notation in eine Uhrzeit.

```stunde```: Property-Attribut, das die Stunde liefert.

```minute```: Property-Attribut, das die Minute liefert.

```sekunde```: Property-Attribut, das die Sekunde liefert.

```__eq__```: Gibt zurueck, ob zwei Uhrzeiten gleich sind.

```__ne__```: Invertiert das Ergebnis der Methode ```__eq__```.

```__lt__```: Gibt zurück, ob die Uhrzeit kleiner als das Argument ist.

```__gt__```: Gibt zurück, ob die Uhrzeit größer als das Argument ist.

```__le_```: Gibt zurück, ob die Uhrzeit kleiner oder gleich dem Argument ist.

```__ge__```: Gibt zurück, ob die Uhrzeit größer oder gleich dem Argument ist.

```__repr__```: Gibt den Representations-String der Uhrzeit zurück.

###Stunde

####Exceptions

* __StundeException__ &rarr; Basisklasse für Exceptions, die mit der Stunde zu tun haben.
* __StundeKeineGanzeZahl__ &rarr; abgeleitet von __UhrzeitException__. Wird ausgelöst, wenn eine Stunde gegeben wird, 
  die kein int-Wert ist.
* __StundeZuGross__ &rarr; abgeleitet von __StundeException__. Wird ausgelöst, 
  wenn eine Stunde, die größer ist als 59, gegeben wird.
* __StundeZuKlein__ &rarr; abgeleitet von __StundeException__. Wird ausgelöst, 
  wenn eine Stunde, die kleiner ist als 0, gegeben wird.
  
####Methoden

```__init__```: Nimmt eine Stunde als int-Wert.

```stunde```: Property-Attribut, das die Stunde als int-Wert liefert.

```__repr__```: Liefert einen Representations-String für das Objekt.

```__str__```: Liefert den zweistelligen Wert der Stunde als String.

```__int__```: Liefert die Stunde als int-Wert.

###Minute

####Exceptions

* __MinuteException__ &rarr; abgeleitet von __UhrzeitException__. 
  Basisklasse für Exceptions, die mit Minuten zusammenhängen.
* __MinuteKeineGanzeZahl__ &rarr; abgeleitet von __MinuteException__. Wird geworfen, 
  wenn eine gegebene Minute keine ganze Zahl ist.
* __MinuteZuGross__ &rarr; abgeleitet von __MinuteException__. Wird geworfen, wenn eine Minute größer als 59 ist.
* __MinuteZuKlein__ &rarr; abgeleitet von __MinuteException__. Wird geworfen, wenn eine Minute kleiner als 0 ist.

####Methoden

```__init__```: Nimmt die Minute als int-Wert.

```minute```: Property-Attribut, das die Minute liefert.

```__repr__```: Liefert den Representations-String für die Minute.

```__str__```: Liefert den zweistelligen String der Minute.

```__int__```: Liefert den Wert der Minute als Integer.

###Sekunde

####Exceptions

* __SekundeExceptions__ &rarr; abgeleitet von __UhrzeitException__. 
  Basisklasse für Exceptions, die mit einer Sekunde zusammenhängen.
* __SekundeKeineGanzeZahl__ &rarr; abgeleitet von __SekundeExceptions__. Wird ausgelöst, 
  wenn die Sekunde keine ganze Zahl ist.
* __SekundeZuGross__ &rarr; abgeleitet von __SekundeZuGross__. Wird ausgelöst, wenn die Sekunde größer als 59 ist.
* __SekundeZuKlein__ &rarr; abgeleitet von __SekundeZuKlein__. Wird ausgelöst, wenn die Sekunde kleiner als 0 ist.

####Methoden

```__init__```: Nimmt die Sekunde als Integer;

```sekunde```: Property-Attribut, das die Sekunde liefert.

```__repr__```: Liefert den Representations-String der Sekunde.

```__str__```: Liefert den zweistelligen String der Sekunde ohne zusätzliche Zeichen. 

```__int__```: Liefert den Wert der Sekunde als Integer.