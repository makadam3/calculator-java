****Prilikom testiranja uzela sam u obzir ulazne vrednosti i očekivane izlazne rezultate. Evo nekoliko testova koje možemo izvršiti na Calculator klasi:**

Osnovne aritmetičke operacije (npr. "2+3", "8-3", "5*4", "10/2") i proveriti da li rezultati odgovaraju očekivanim vrednostima.

Složeni izrazi (npr. "5+32-8/4", "25-3/6+7") i proveriti da li se rezultati pravilno izračunavaju.

Deljenje nulom (npr. "5/0") i proveriti da li se pravilno vraća "Infinity" bez grešaka.

Negativna beskonačnost(npr. "-2/0") i proveriti da li se pravilno vraća "-Infinity" bez grešaka.

Nevalidan unos (npr. "abc") i proveriti da li se vraća "ERROR".

Korišćenje različitih operatora (npr. "5+3*2/6-4") i proveriti da li se rezultati pravilno izračunavaju.

Testiranje granica - Testirati kako se aplikacija ponaša sa veoma velikim ili veoma malim brojevima, kao i sa velikim brojevima aritmetičkih operacija.

Testiranje performansi - Izmeriti vreme izvršavanja za velike i složene izraze kako bismo proverili performanse aplikacije.

Testiranje praznog unosa - Uneti prazan izraz i proveriti kako se aplikacija ponaša.

Testiranje višestrukih uzastopnih operatora (npr. "5++3", "4*-2") i proveriti kako se aplikacija nosi s tim.

Testiranje različitih kombinacija negativnih brojeva (npr. "5--3", "4*-2", "-5*-3") i proveriti da li se pravilno izračunavaju.

Testiranje različitih kombinacija beskonačnosti (npr. "Infinity+5", "-Infinity/2") i proveriti da li se pravilno obrađuju.


****Jedinicni test korisccenjem JUnit alata(automatizacijom):**

import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

public class CalculatorTest {

    @Test
    public void testCalculateAddition() {
        String expression = "2+3";
        String expected = "5.0";
        String result = Calculator.Run(expression);
        assertEquals(expected, result);
    }

    @Test
    public void testCalculateSubtraction() {
        String expression = "8-3";
        String expected = "5.0";
        String result = Calculator.Run(expression);
        assertEquals(expected, result);
    }

    @Test
    public void testCalculateMultiplication() {
        String expression = "5*4";
        String expected = "20.0";
        String result = Calculator.Run(expression);
        assertEquals(expected, result);
    }

    @Test
    public void testCalculateDivision() {
        String expression = "10/2";
        String expected = "5.0";
        String result = Calculator.Run(expression);
        assertEquals(expected, result);
    }

    @Test
    public void testCalculateComplexExpression() {
        String expression = "5+3*2-8/4";
        String expected = "10.0";
        String result = Calculator.Run(expression);
        assertEquals(expected, result);
    }

    @Test
    public void testCalculateInvalidExpression() {
        String expression = "5+3/0";
        String expected = "ERROR";
        String result = Calculator.Run(expression);
        assertEquals(expected, result);
    }

    @Test
    public void testCalculateInfinity() {
        String expression = "1/0";
        String expected = "Infinity";
        String result = Calculator.Run(expression);
        assertEquals(expected, result);
    }

    @Test
    public void testCalculateNegativeInfinity() {
        String expression = "-1/0";
        String expected = "-Infinity";
        String result = Calculator.Run(expression);
        assertEquals(expected, result);
    }
}

****Nedostaci, problemi i zapažanja:**

Nedostatak Obrade Grešaka: Kod nedovoljno rukuje neispravnim unosima. Kada korisnik unese nevalidan izraz ili dođe do greške u parsiranju brojeva, kod jednostavno vraća "ERROR" bez detaljnog objašnjenja o prirodi greške. Bilo bi bolje pružiti preciznije informacije o prirodi greške kako bi korisnik mogao bolje razumeti i ispraviti svoj unos.

Nedoslednosti u Obradi Beskonačnosti: Kod koristi "-Infinity" i "Infinity" za označavanje negativne i pozitivne beskonačnosti. To može biti potencijalno problematično i može dovesti do neželjenog ponašanja. Trebalo bi dodatno razmotriti kako se beskonačnosti tretiraju i koriste u izračunavanju.

Nedoslednosti u Manipulaciji Nizovima: Postoje delovi koda gde se često dodaju i uklanjaju elementi iz lista numbers i operations. Ovo može biti zamorno i potencijalno prouzrokovati greške ako se operacije ne izvršavaju tačno u određenom redosledu. Trebalo bi razmotriti bolji pristup obradi i organizaciji ovih lista.

Nedoslednosti u Imenovanju: Iako klasa Operations definiše operatore kao karaktere, metoda ToString() vraća string. Ovo može dovesti do konfuzije pri čitanju koda. Trebalo bi uskladiti tipove i vrednosti kako bi kod bio konzistentniji.

Složenost Calculate Metode: Metoda Calculate ima složenu strukturu sa nizovima uslova za određivanje operacija. Ovo otežava razumevanje i održavanje koda. Nedoslednosti i potencijalni bugovi mogu se pojaviti ako nije jasno definisano redosled operacija ili ako se pojave specifične situacije koje nisu obuhvaćene. Treba razmotriti pojednostavljenje ove metode.
