# junit-course

JUnit 5 è la più recente versione del famoso framework di testing per il linguaggio di programmazione Java. Questa nuova versione introduce una serie di nuove funzionalità e miglioramenti, rendendo il processo di testing più flessibile, leggibile ed efficiente.

JUnit 5 si basa su un'architettura modulare che permette ai programmatori di selezionare solo le funzionalità di cui hanno bisogno, invece di dover includere tutto il framework. Questa flessibilità offre un maggiore controllo e facilità di utilizzo per gli sviluppatori.

Inoltre, JUnit 5 introduce anche nuove annotazioni che permettono di scrivere test più chiari e leggibili, migliorando la manutenibilità del codice. Le nuove annotazioni forniscono un approccio più dichiarativo nei test, favorendo una maggiore comprensione degli intenti dei test stessi.



JUnit 5 è stato introdotto come una nuova versione di JUnit per Java, con nuovi tag che permettono di scrivere test in modo più efficiente e flessibile. Di seguito sono elencati alcuni dei principali tag di JUnit 5 insieme a degli esempi di codice:

    @Test: Questo tag viene utilizzato per annotare i metodi dei test. Indica che il metodo annotato è un metodo di test e deve essere eseguito durante l'esecuzione dei test.

Esempio:


```
@Test
void testAddition() {
   Calculator calculator = new Calculator();
   int result = calculator.add(2, 3);
   assertEquals(5, result);
}
```

@BeforeEach: Questo tag viene utilizzato per annotare i metodi che devono essere eseguiti prima di ogni test. Viene spesso utilizzato per inizializzare alcuni oggetti o variabili necessarie per eseguire i test.

Esempio:

```
@BeforeEach
void setup() {
   // Inizializza gli oggetti o le variabili necessarie per i test
   // ad esempio, creazione di istanze di oggetti o inizializzazione di variabili
   calculator = new Calculator();
}
```


@AfterEach: Questo tag viene utilizzato per annotare i metodi che devono essere eseguiti dopo ogni test. Viene spesso utilizzato per eseguire ripristini o pulizie dopo aver completato un test.

Esempio:
```
@AfterEach
void tearDown() {
   // Esegui ripristini o pulizie dopo aver completato un test
   // ad esempio, deallocazione di risorse o pulizia di dati
   calculator = null;
}
```
@DisplayName: Questo tag viene utilizzato per fornire un nome personalizzato per il test nel report dei test. Può essere utile per descrivere in modo più chiaro l'obiettivo del test.

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
Questi sono solo alcuni dei principali tag disponibili in JUnit 5. Ci sono anche altri tag come @BeforeAll, @AfterAll, @Disabled, @ParameterizedTest, ecc. che possono essere utilizzati per diversi scopi durante la scrittura dei test.
