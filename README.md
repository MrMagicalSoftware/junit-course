# junit-course

JUnit 5 è la più recente versione del famoso framework di testing per il linguaggio di programmazione Java. Questa nuova versione introduce una serie di nuove funzionalità e miglioramenti, rendendo il processo di testing più flessibile, leggibile ed efficiente.

JUnit 5 si basa su un'architettura modulare che permette ai programmatori di selezionare solo le funzionalità di cui hanno bisogno, invece di dover includere tutto il framework. Questa flessibilità offre un maggiore controllo e facilità di utilizzo per gli sviluppatori.

Inoltre, JUnit 5 introduce anche nuove annotazioni che permettono di scrivere test più chiari e leggibili, migliorando la manutenibilità del codice. Le nuove annotazioni forniscono un approccio più dichiarativo nei test, favorendo una maggiore comprensione degli intenti dei test stessi.



JUnit 5 è stato introdotto come una nuova versione di JUnit per Java, con nuovi tag che permettono di scrivere test in modo più efficiente e flessibile. Di seguito sono elencati alcuni dei principali tag di JUnit 5 insieme a degli esempi di codice:

Test: Questo tag viene utilizzato per annotare i metodi dei test. Indica che il metodo annotato è un metodo di test e deve essere eseguito durante l'esecuzione dei test.

Esempio:


```
@Test
void testAddition() {
   Calculator calculator = new Calculator();
   int result = calculator.add(2, 3);
   assertEquals(5, result);
}
```

**BeforeEach**: Questo tag viene utilizzato per annotare i metodi che devono essere eseguiti prima di ogni test. Viene spesso utilizzato per inizializzare alcuni oggetti o variabili necessarie per eseguire i test.

Esempio:

```
@BeforeEach
void setup() {
   // Inizializza gli oggetti o le variabili necessarie per i test
   // ad esempio, creazione di istanze di oggetti o inizializzazione di variabili
   calculator = new Calculator();
}
```


**AfterEach**: Questo tag viene utilizzato per annotare i metodi che devono essere eseguiti dopo ogni test. Viene spesso utilizzato per eseguire ripristini o pulizie dopo aver completato un test.

Esempio:
```
@AfterEach
void tearDown() {
   // Esegui ripristini o pulizie dopo aver completato un test
   // ad esempio, deallocazione di risorse o pulizia di dati
   calculator = null;
}
```


**DisplayName**: Questo tag viene utilizzato per fornire un nome personalizzato per il test nel report dei test. Può essere utile per descrivere in modo più chiaro l'obiettivo del test.

Esempio:

```
@Test
@DisplayName("Test addizione")
void testAddition() {
   Calculator calculator = new Calculator();
   int result = calculator.add(2, 3);
   assertEquals(5, result);
}
```

_______________________________________________________


| Annotation	 | Description    | 
| :---:   | :---: |
| @Test   | Denotes that a method is a test method. Unlike JUnit 4’s @Test annotation, this annotation does not declare any attributes, since test extensions in JUnit Jupiter operate based on their own dedicated annotations. Such methods are inherited unless they are overridden.|
| @ParameterizedTest| Denotes that a method is a parameterized test. Such methods are inherited unless they are overridden.|
| @RepeatedTest| Denotes that a method is a test template for a repeated test. Such methods are inherited unless they are overridden.|
| @TestFactory| Denotes that a method is a test factory for dynamic tests. Such methods are inherited unless they are overridden.|
| @TestTemplate| Denotes that a method is a template for test cases designed to be invoked multiple times depending on the number of invocation contexts returned by the registered providers. Such methods are inherited unless they are overridden.|
| @TestClassOrder| Used to configure the test class execution order for @Nested test classes in the annotated test class. Such annotations are inherited.|
| @TestMethodOrder|Used to configure the test method execution order for the annotated test class; similar to JUnit 4’s @FixMethodOrder. Such annotations are inherited.|
| @TestInstance|Used to configure the test instance lifecycle for the annotated test class. Such annotations are inherited.|
| @DisplayName|Declares a custom display name for the test class or test method. Such annotations are not inherited.|
| @DisplayNameGeneration| Declares a custom display name generator for the test class. Such annotations are inherited.|
| @BeforeEach|	Denotes that the annotated method should be executed before each @Test, @RepeatedTest, @ParameterizedTest, or @TestFactory method in the current class; analogous to JUnit 4’s @Before. Such methods are inherited – unless they are overridden or superseded (i.e., replaced based on signature only, irrespective of Java’s visibility rules).|
| @AfterEach|Denotes that the annotated method should be executed after each @Test, @RepeatedTest, @ParameterizedTest, or @TestFactory method in the current class; analogous to JUnit 4’s @After. Such methods are inherited – unless they are overridden or superseded (i.e., replaced based on signature only, irrespective of Java’s visibility rules).|
| @BeforeAll|Denotes that the annotated method should be executed before all @Test, @RepeatedTest, @ParameterizedTest, and @TestFactory methods in the current class; analogous to JUnit 4’s @BeforeClass. Such methods are inherited – unless they are hidden, overridden, or superseded, (i.e., replaced based on signature only, irrespective of Java’s visibility rules) – and must be static unless the "per-class" test instance lifecycle is used.|
| @AfterAll|Denotes that the annotated method should be executed after all @Test, @RepeatedTest, @ParameterizedTest, and @TestFactory methods in the current class; analogous to JUnit 4’s @AfterClass. Such methods are inherited – unless they are hidden, overridden, or superseded, (i.e., replaced based on signature only, irrespective of Java’s visibility rules) – and must be static unless the "per-class" test instance lifecycle is used.|
| @Nested|Denotes that the annotated class is a non-static nested test class. On Java 8 through Java 15, @BeforeAll and @AfterAll methods cannot be used directly in a @Nested test class unless the "per-class" test instance lifecycle is used. Beginning with Java 16, @BeforeAll and @AfterAll methods can be declared as static in a @Nested test class with either test instance lifecycle mode. Such annotations are not inherited.|
| @Tag|Used to declare tags for filtering tests, either at the class or method level; analogous to test groups in TestNG or Categories in JUnit 4. Such annotations are inherited at the class level but not at the method level.|
| @Disabled |Used to disable a test class or test method; analogous to JUnit 4’s @Ignore. Such annotations are not inherited.|
| @Timeout |Used to fail a test, test factory, test template, or lifecycle method if its execution exceeds a given duration. Such annotations are inherited.|
| @Timeout |Used to fail a test, test factory, test template, or lifecycle method if its execution exceeds a given duration. Such annotations are inherited.
| @ExtendWith |Used to register extensions declaratively. Such annotations are inherited.|
| @RegisterExtension |Used to register extensions programmatically via fields. Such fields are inherited unless they are shadowed.|
| @TempDir|Used to supply a temporary directory via field injection or parameter injection in a lifecycle method or test method; located in the org.junit.jupiter.api.io package.|



____________________________________________


## BeforeAll

L'annotazione @BeforeAll in JUnit 5 indica che un metodo statico deve essere eseguito una sola volta prima di tutti i test nella classe. È utile quando hai bisogno di inizializzare dati o risorse globali che sono comuni a tutti i test della classe. Ecco un esempio di come utilizzare @BeforeAll:

import org.junit.jupiter.api.BeforeAll;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class CalcolatriceTest {

    private static Calcolatrice calcolatrice;

    @BeforeAll
    static void setUpBeforeClass() {
        // Inizializzazione della calcolatrice una sola volta
        calcolatrice = new Calcolatrice();
        System.out.println("Inizializzazione della calcolatrice");
    }

    @Test
    void testSomma() {
        int risultato = calcolatrice.somma(3, 5);
        assertEquals(8, risultato);
    }

    @Test
    void testSottrazione() {
        int risultato = calcolatrice.sottrazione(10, 4);
        assertEquals(6, risultato);
    }
}


In questo esempio, abbiamo una classe di test CalcolatriceTest che testa i metodi di una classe Calcolatrice. L'annotazione @BeforeAll è utilizzata per inizializzare l'istanza della calcolatrice calcolatrice prima dell'esecuzione di qualsiasi test. Questo metodo verrà eseguito una sola volta all'inizio, prima di qualsiasi test all'interno della classe di test.

Questo approccio è utile quando hai risorse costose da inizializzare, come connessioni al database o oggetti complessi, che possono essere condivisi tra i tuoi test. Assicurati che il metodo annotato con @BeforeAll sia statico e che le risorse inizializzate siano dichiarate come variabili statiche, in modo che possano essere condivise tra tutti i test senza la necessità di reinizializzarle per ciascun test.


_____________________

## ParameterizedTest


L'annotazione `@ParameterizedTest` in JUnit 5 ti permette di eseguire lo stesso test con diversi set di dati di input. Questo è particolarmente utile quando vuoi eseguire un test su molte combinazioni di dati per verificare che la tua logica funzioni correttamente. Ecco un esempio di come utilizzare `@ParameterizedTest`:

Supponiamo di avere una classe `Calcolatrice` con un metodo `somma` che vogliamo testare con input diversi.

```
import org.junit.jupiter.api.Test;
import org.junit.jupiter.params.ParameterizedTest;
import org.junit.jupiter.params.provider.CsvSource;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class CalcolatriceTest {

    private Calcolatrice calcolatrice = new Calcolatrice();

    @ParameterizedTest
    @CsvSource({
        "2, 3, 5",
        "0, 0, 0",
        "-1, 1, 0",
        "-2, -3, -5"
    })
    void testSomma(int a, int b, int risultatoAspettato) {
        int risultato = calcolatrice.somma(a, b);
        assertEquals(risultatoAspettato, risultato);
    }
}
```

In questo esempio, abbiamo utilizzato `@ParameterizedTest` in combinazione con `@CsvSource` per specificare diversi set di input e i risultati attesi. Il test `testSomma` verrà eseguito quattro volte, una volta per ciascun set di input specificato nella `@CsvSource`. Il test verifica che il risultato della somma ottenuto dal metodo `calcolatrice.somma` corrisponda al risultato aspettato.

Il formato `@CsvSource` consente di definire facilmente molteplici casi di test fornendo input e risultati attesi in un formato tabellare. Puoi anche utilizzare altre sorgenti di parametri come `@MethodSource` o `@ValueSource` in base alle tue esigenze specifiche.


_______________________________________________________________________



## RepeatedTest



L'annotazione @RepeatedTest in JUnit 5 ti permette di eseguire lo stesso test un numero specifico di volte. Questo può essere utile per verificare la stabilità e la ripetibilità di un test, soprattutto quando stai cercando di identificare problemi sporadici o di testare la robustezza del tuo codice. Ecco un esempio di come utilizzare @RepeatedTest:

Supponiamo di avere un metodo eseguiOperazioneCostosa che vogliamo testare 10 volte.

import org.junit.jupiter.api.RepeatedTest;
import org.junit.jupiter.api.TestInstance;
import static org.junit.jupiter.api.TestInstance.Lifecycle;
import static org.junit.jupiter.api.Assertions.assertTrue;

@TestInstance(Lifecycle.PER_CLASS)
public class OperazioneCostosaTest {

    private int numeroEsecuzioni = 0;

    @RepeatedTest(10)
    void testEsecuzioneRipetuta() {
        numeroEsecuzioni++;
        System.out.println("Esecuzione #" + numeroEsecuzioni);
        boolean risultato = eseguiOperazioneCostosa();
        assertTrue(risultato);
    }

    private boolean eseguiOperazioneCostosa() {
        // Simuliamo un'operazione costosa
        return true;
    }
}


In questo esempio, stiamo testando il metodo eseguiOperazioneCostosa 10 volte utilizzando @RepeatedTest(10). La variabile numeroEsecuzioni tiene traccia del numero di esecuzioni, e il test verifica che il risultato di eseguiOperazioneCostosa sia sempre true.

L'annotazione @TestInstance(Lifecycle.PER_CLASS) è stata utilizzata per dichiarare che la classe di test mantiene una singola istanza per l'intera classe, consentendo così di mantenere lo stato tra le esecuzioni ripetute. Inoltre, @RepeatedTest può essere utilizzato anche con altri parametri, come name per dare un nome specifico al test ripetuto o displayName per personalizzare il nome visualizzato nel report di test.


_______________________________________






## TestFactory


L'annotazione `@TestFactory` in JUnit 5 consente di creare test in modo dinamico al momento dell'esecuzione. È utile quando il numero o la configurazione dei test dipende da dati o logica complessa. Ecco un esempio di come utilizzare `@TestFactory`:

Supponiamo di avere una classe `Calcolatrice` con un metodo `somma` che vogliamo testare con diverse combinazioni di input.

```
import org.junit.jupiter.api.TestFactory;
import org.junit.jupiter.api.DynamicTest;
import org.junit.jupiter.api.function.Executable;
import static org.junit.jupiter.api.Assertions.assertEquals;
import java.util.Arrays;
import java.util.Collection;
import java.util.stream.Stream;

public class CalcolatriceTest {

    private Calcolatrice calcolatrice = new Calcolatrice();

    @TestFactory
    Collection<DynamicTest> testSomma() {
        return Arrays.asList(
            dynamicTest("Test somma positiva", 2, 3, 5),
            dynamicTest("Test somma zero", 0, 0, 0),
            dynamicTest("Test somma negativa", -1, 1, 0),
            dynamicTest("Test somma negativa con negativo", -2, -3, -5)
        );
    }

    private DynamicTest dynamicTest(String nome, int a, int b, int risultatoAspettato) {
        Executable eseguiTest = () -> {
            int risultato = calcolatrice.somma(a, b);
            assertEquals(risultatoAspettato, risultato);
        };

        return DynamicTest.dynamicTest(nome, eseguiTest);
    }
}

```

In questo esempio, stiamo usando `@TestFactory` per creare dinamicamente una collezione di test. La collezione contiene una serie di test dinamici definiti nella funzione `testSomma`. Ogni test dinamico è creato chiamando il metodo `dynamicTest`, che prende il nome del test e una lambda che contiene il codice effettivo del test.

I test dinamici vengono eseguiti e il risultato viene riportato nel report dei test. Questo approccio è utile quando hai bisogno di testare una serie di casi di test simili con dati diversi, in modo da evitare la duplicazione del codice di test e rendere il tuo codice più leggibile ed estensibile.



___________________________


## BeforeEach

L'annotazione `@BeforeEach` in JUnit 5 indica che un metodo deve essere eseguito prima di ciascun test nella classe. Questo è utile quando hai bisogno di inizializzare dati o risorse comuni a tutti i test, garantendo che ogni test parta da uno stato coerente. Ecco un esempio di come utilizzare `@BeforeEach`:

Supponiamo di avere una classe `Account` con un metodo `preleva` che vogliamo testare. Prima di ogni test, vogliamo creare un nuovo account e depositare un ammontare iniziale.

```java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class AccountTest {

    private Account account;

    @BeforeEach
    void setUp() {
        // Inizializziamo un nuovo account prima di ogni test
        account = new Account("12345", 1000); // Numero dell'account e saldo iniziale
    }

    @Test
    void testPrelevaConSaldoSufficiente() {
        boolean prelievoRiuscito = account.preleva(500);
        assertEquals(500, account.getSaldo());
        assertEquals(true, prelievoRiuscito);
    }

    @Test
    void testPrelevaConSaldoInsufficiente() {
        boolean prelievoRiuscito = account.preleva(1500);
        assertEquals(1000, account.getSaldo()); // Il saldo non cambia
        assertEquals(false, prelievoRiuscito);
    }
}
```

In questo esempio, utilizziamo `@BeforeEach` per garantire che l'istanza dell'account `account` venga creata prima di ogni test. Questo assicura che ogni test parta da uno stato pulito e indipendente dagli altri test.

I due metodi di test `testPrelevaConSaldoSufficiente` e `testPrelevaConSaldoInsufficiente` verificano il comportamento del metodo `preleva` dell'account in due situazioni diverse.

Utilizzando `@BeforeEach`, è possibile garantire che i test siano ripetibili e non influiscano l'uno sull'altro a causa di dati condivisi.



_____________________________________________


## AfterEach

L'annotazione `@AfterEach` in JUnit 5 indica che un metodo deve essere eseguito dopo ciascun test nella classe. Questo è utile per effettuare operazioni di pulizia o rilascio di risorse dopo l'esecuzione di ciascun test, garantendo che ogni test non lasci alcun impatto sugli altri. Ecco un esempio di come utilizzare `@AfterEach`:

Supponiamo di avere una classe `DatabaseManager` che gestisce una connessione al database e vogliamo assicurarci di chiudere la connessione dopo ciascun test.

```java
import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class DatabaseManagerTest {

    private DatabaseManager databaseManager;
    private boolean databaseConnected;

    @BeforeEach
    void setUp() {
        // Inizializziamo il database manager e apriamo la connessione prima di ogni test
        databaseManager = new DatabaseManager();
        databaseConnected = databaseManager.connectToDatabase();
    }

    @Test
    void testInserimentoDati() {
        // Test per inserire dati nel database
        boolean inserimentoRiuscito = databaseManager.inserisciDati("dati di prova");
        assertEquals(true, inserimentoRiuscito);
    }

    @Test
    void testLetturaDati() {
        // Test per leggere dati dal database
        String datiLetti = databaseManager.leggiDati();
        assertEquals("dati di prova", datiLetti);
    }

    @AfterEach
    void tearDown() {
        // Chiudiamo la connessione al database dopo ogni test
        if (databaseConnected) {
            databaseManager.disconnectFromDatabase();
            databaseConnected = false;
        }
    }
}
```

In questo esempio, utilizziamo `@AfterEach` per garantire che la connessione al database venga chiusa dopo l'esecuzione di ciascun test. Il metodo `tearDown` viene eseguito dopo ogni test e verifica se la connessione è aperta; se lo è, chiude la connessione.

Questo approccio garantisce che ciascun test inizi con una connessione aperta e termini con una connessione chiusa, evitando così che i test influiscano l'uno sull'altro o lascino la connessione aperta accidentalmente.



_________________________________________________


L'annotazione `@AfterAll` in JUnit 5 indica che un metodo statico deve essere eseguito una sola volta dopo l'esecuzione di tutti i test nella classe. Questo è utile quando hai bisogno di effettuare operazioni di pulizia o rilascio di risorse una volta completati tutti i test. Ecco un esempio di come utilizzare `@AfterAll`:

Supponiamo di avere una classe `ResourceHandler` che gestisce una risorsa globale e vogliamo assicurarci di rilasciare questa risorsa una volta completati tutti i test.

```java
import org.junit.jupiter.api.AfterAll;
import org.junit.jupiter.api.BeforeAll;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class ResourceHandlerTest {

    private static ResourceHandler resourceHandler;
    private static boolean resourceInitialized;

    @BeforeAll
    static void setUpBeforeClass() {
        // Inizializziamo la risorsa una sola volta prima di tutti i test
        resourceHandler = new ResourceHandler();
        resourceInitialized = resourceHandler.initializeResource();
    }

    @Test
    void testOperazioneRisorsa() {
        // Test per eseguire un'operazione sulla risorsa
        boolean operazioneRiuscita = resourceHandler.performResourceOperation();
        assertEquals(true, operazioneRiuscita);
    }

    @AfterAll
    static void tearDownAfterClass() {
        // Rilasciamo la risorsa dopo tutti i test
        if (resourceInitialized) {
            resourceHandler.releaseResource();
            resourceInitialized = false;
        }
    }
}
```

In questo esempio, utilizziamo `@BeforeAll` per garantire che la risorsa venga inizializzata una sola volta prima dell'esecuzione di tutti i test. Utilizziamo `@AfterAll` per rilasciare la risorsa dopo che tutti i test sono stati eseguiti.

Questo approccio è utile quando hai bisogno di risorse globali per l'intera classe di test e desideri garantire che queste risorse vengano correttamente inizializzate prima dei test e rilasciate alla fine. L'uso di `@AfterAll` è particolarmente utile quando si tratta di risorse come connessioni al database o file temporanei che devono essere puliti quando tutti i test sono stati eseguiti.


_______________________________

## NESTED

L'annotazione `@Nested` in JUnit 5 permette di creare classi di test nidificate all'interno di una classe di test principale. Questo è utile per organizzare i test in una struttura gerarchica e separare i test correlati in classi nidificate. Ecco un esempio di come utilizzare `@Nested`:

Supponiamo di avere una classe `Calculator` che vogliamo testare. Possiamo organizzare i test in classi nidificate per coprire diversi aspetti della calcolatrice, come l'addizione e la sottrazione:

```java
import org.junit.jupiter.api.Nested;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class CalculatorTest {

    @Nested
    class AddTest {

        @Test
        void testAdditionPositiveNumbers() {
            Calculator calculator = new Calculator();
            int result = calculator.add(3, 5);
            assertEquals(8, result);
        }

        @Test
        void testAdditionNegativeNumbers() {
            Calculator calculator = new Calculator();
            int result = calculator.add(-3, -5);
            assertEquals(-8, result);
        }
    }

    @Nested
    class SubtractTest {

        @Test
        void testSubtractionPositiveNumbers() {
            Calculator calculator = new Calculator();
            int result = calculator.subtract(10, 3);
            assertEquals(7, result);
        }

        @Test
        void testSubtractionNegativeNumbers() {
            Calculator calculator = new Calculator();
            int result = calculator.subtract(-10, -3);
            assertEquals(-7, result);
        }
    }
}
```

In questo esempio, abbiamo una classe `CalculatorTest` con due classi nidificate: `AddTest` e `SubtractTest`. Ogni classe nidificata contiene una serie di test relativi all'addizione o alla sottrazione, rispettivamente.

L'uso di classi nidificate aiuta a organizzare i test in modo più chiaro e a mantenere una struttura gerarchica logica. Questo è particolarmente utile quando si hanno molte suite di test e si desidera separare concetti e comportamenti specifici in classi di test indipendenti.


__________________________________________



L'annotazione `@Tag` in JUnit 5 consente di contrassegnare i test con etichette (tag) per classificarli in base a determinati criteri. Questo è utile per eseguire o escludere gruppi specifici di test in base alle loro etichette o per applicare filtri ai test in base alle etichette durante l'esecuzione. Ecco un esempio di come utilizzare `@Tag`:

Supponiamo di avere una classe `Calculator` che vogliamo testare e vogliamo contrassegnare alcuni test come "operazioni di base" e altri come "operazioni avanzate":

```java
import org.junit.jupiter.api.Tag;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class CalculatorTest {

    @Test
    @Tag("basic")
    void testAddition() {
        Calculator calculator = new Calculator();
        int result = calculator.add(3, 5);
        assertEquals(8, result);
    }

    @Test
    @Tag("basic")
    void testSubtraction() {
        Calculator calculator = new Calculator();
        int result = calculator.subtract(10, 3);
        assertEquals(7, result);
    }

    @Test
    @Tag("advanced")
    void testMultiplication() {
        Calculator calculator = new Calculator();
        int result = calculator.multiply(4, 6);
        assertEquals(24, result);
    }

    @Test
    @Tag("advanced")
    void testDivision() {
        Calculator calculator = new Calculator();
        double result = calculator.divide(20, 4);
        assertEquals(5.0, result, 0.0001);
    }
}
```

In questo esempio, abbiamo utilizzato `@Tag` per contrassegnare i test con etichette "basic" e "advanced". I test di addizione e sottrazione sono contrassegnati come "basic", mentre i test di moltiplicazione e divisione sono contrassegnati come "advanced".

Puoi ora utilizzare queste etichette per eseguire o escludere gruppi specifici di test utilizzando i filtri durante l'esecuzione dei test. Ad esempio, puoi eseguire solo i test contrassegnati come "basic" o "advanced" secondo le tue esigenze.

______________________________

L'annotazione `@Timeout` in JUnit 5 consente di definire un limite di tempo massimo per l'esecuzione di un test. Se un test supera il limite di tempo specificato, verrà segnalato come fallito. Questo è utile per garantire che i tuoi test non rimangano bloccati indefinitamente e per individuare potenziali problemi di prestazioni o di sincronizzazione nel tuo codice. Ecco un esempio di come utilizzare `@Timeout`:

```java
import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.Timeout;

public class TimeoutExample {

    @Test
    @Timeout(2) // Limite di tempo di 2 secondi
    void testEsecuzioneRapida() {
        // Simuliamo un'operazione che dovrebbe essere eseguita in meno di 2 secondi
        doSomethingQuick();
    }

    @Test
    @Timeout(5) // Limite di tempo di 5 secondi
    void testEsecuzioneLenta() {
        // Simuliamo un'operazione che richiede più di 5 secondi
        doSomethingSlow();
    }

    private void doSomethingQuick() {
        // Operazione rapida
    }

    private void doSomethingSlow() {
        try {
            Thread.sleep(6000); // Simuliamo un'operazione lenta di 6 secondi
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```

In questo esempio, abbiamo due test: `testEsecuzioneRapida` e `testEsecuzioneLenta`. Il primo test ha un limite di tempo di 2 secondi, il secondo di 5 secondi.

Il test `testEsecuzioneRapida` eseguirà con successo poiché `doSomethingQuick` è un'operazione rapida che completa entro il limite di tempo specificato.

Il test `testEsecuzioneLenta`, d'altra parte, supererà il limite di tempo specificato poiché `doSomethingSlow` è un'operazione lenta che richiede più di 5 secondi per essere completata. In questo caso, il test verrà segnalato come fallito.

L'uso di `@Timeout` è utile per garantire che i tuoi test non rimangano bloccati e per individuare eventuali problemi di performance nel tuo codice. Puoi regolare il limite di tempo in base alle esigenze del tuo test.


____________________________________________


## ExtendWith 



L'annotazione `@ExtendWith` in JUnit 5 consente di estendere il comportamento del framework di test. Puoi utilizzare `@ExtendWith` per collegare estensioni personalizzate a livello di classe o metodo. Ecco un esempio di come utilizzare `@ExtendWith` con un'estensione personalizzata:

Supponiamo di avere una classe di test `CalculatorTest` e vogliamo utilizzare un'**estensione personalizzata** chiamata `CustomExtension` per effettuare operazioni personalizzate prima e dopo l'esecuzione dei test.

```java
import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.extension.ExtendWith;

@ExtendWith(CustomExtension.class)
public class CalculatorTest {

    @Test
    void testAddition() {
        Calculator calculator = new Calculator();
        int result = calculator.add(3, 5);
        assertEquals(8, result);
    }

    @Test
    void testSubtraction() {
        Calculator calculator = new Calculator();
        int result = calculator.subtract(10, 3);
        assertEquals(7, result);
    }
}
```

In questo esempio, abbiamo contrassegnato la classe `CalculatorTest` con `@ExtendWith(CustomExtension.class)`, indicando che vogliamo utilizzare l'estensione personalizzata `CustomExtension` con questa classe di test.

Ora creiamo l'estensione personalizzata `CustomExtension`. Per farlo, creiamo una classe che implementi l'interfaccia `Extension` di JUnit 5 e sovrascriviamo i metodi necessari, come `beforeEach` e `afterEach`, per eseguire operazioni personalizzate prima e dopo ogni test. Ecco un esempio:

```java
import org.junit.jupiter.api.extension.BeforeEachCallback;
import org.junit.jupiter.api.extension.ExtensionContext;
import org.junit.jupiter.api.extension.ExtensionContext.Namespace;
import org.junit.jupiter.api.extension.ExtensionContext.Store;

public class CustomExtension implements BeforeEachCallback {

    @Override
    public void beforeEach(ExtensionContext context) throws Exception {
        // Operazioni personalizzate da eseguire prima di ogni test
        String testName = context.getRequiredTestMethod().getName();
        System.out.println("Esecuzione di " + testName);
        
        // Puoi anche archiviare dati condivisi tra i test nel contesto
        Store store = context.getStore(Namespace.create(getClass(), testName));
        store.put("chiave", "valore");
    }
}
```

In questa estensione personalizzata, stiamo semplicemente stampando il nome del test prima dell'esecuzione di ciascun test e mettendo un dato condiviso nel contesto dell'estensione. Puoi personalizzare l'estensione per eseguire le operazioni desiderate prima o dopo i test in base alle tue esigenze.

L'uso di `@ExtendWith` e delle estensioni personalizzate è utile per aggiungere comportamenti personalizzati ai tuoi test o per configurare ambienti di test specifici.


____________________________



L'annotazione `@TempDir` in JUnit 5 è utilizzata per ottenere una directory temporanea per l'uso nei tuoi test. Questo è utile quando devi scrivere o leggere file temporanei durante l'esecuzione dei test senza dover preoccuparti di pulire o gestire manualmente la directory temporanea. Ecco un esempio di come utilizzare `@TempDir`:

```java
import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.io.TempDir;

import java.io.File;
import java.io.IOException;
import java.nio.file.Path;
import java.nio.file.StandardOpenOption;
import java.nio.file.Files;
import java.nio.file.Paths;

import static org.junit.jupiter.api.Assertions.assertTrue;

public class TempDirExample {

    @Test
    void testReadWriteWithTempDir(@TempDir Path tempDir) throws IOException {
        // Ogni test riceve una directory temporanea unica

        // Verifica che la directory temporanea sia stata creata
        assertTrue(Files.exists(tempDir));

        // Scrivi un file temporaneo nella directory
        Path tempFile = tempDir.resolve("tempFile.txt");
        Files.write(tempFile, "Contenuto del file temporaneo".getBytes(), StandardOpenOption.CREATE);

        // Verifica che il file sia stato creato
        assertTrue(Files.exists(tempFile));

        // Leggi il contenuto del file temporaneo
        String content = Files.readString(tempFile);

        // Verifica il contenuto del file
        assertTrue(content.contains("Contenuto del file temporaneo"));
    }
}
```

In questo esempio, abbiamo contrassegnato il parametro `@TempDir` del metodo di test `testReadWriteWithTempDir` con l'annotazione `@TempDir`. JUnit 5 fornirà automaticamente una directory temporanea unica come valore per questo parametro quando il test viene eseguito.

All'interno del test, verifichiamo che la directory temporanea esista, creiamo un file temporaneo all'interno di essa, verifichiamo che il file sia stato creato e leggiamo il contenuto del file temporaneo. L'utilizzo di `@TempDir` semplifica la gestione delle directory temporanee nei tuoi test e rende il tuo codice più pulito e manutenibile.














