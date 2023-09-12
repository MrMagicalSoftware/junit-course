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



Annotation	Description
@Test

Denotes that a method is a test method. Unlike JUnit 4’s @Test annotation, this annotation does not declare any attributes, since test extensions in JUnit Jupiter operate based on their own dedicated annotations. Such methods are inherited unless they are overridden.

@ParameterizedTest

Denotes that a method is a parameterized test. Such methods are inherited unless they are overridden.

@RepeatedTest

Denotes that a method is a test template for a repeated test. Such methods are inherited unless they are overridden.

@TestFactory

Denotes that a method is a test factory for dynamic tests. Such methods are inherited unless they are overridden.

@TestTemplate

Denotes that a method is a template for test cases designed to be invoked multiple times depending on the number of invocation contexts returned by the registered providers. Such methods are inherited unless they are overridden.

@TestClassOrder

Used to configure the test class execution order for @Nested test classes in the annotated test class. Such annotations are inherited.

@TestMethodOrder

Used to configure the test method execution order for the annotated test class; similar to JUnit 4’s @FixMethodOrder. Such annotations are inherited.

@TestInstance

Used to configure the test instance lifecycle for the annotated test class. Such annotations are inherited.

@DisplayName

Declares a custom display name for the test class or test method. Such annotations are not inherited.

@DisplayNameGeneration

Declares a custom display name generator for the test class. Such annotations are inherited.

@BeforeEach

Denotes that the annotated method should be executed before each @Test, @RepeatedTest, @ParameterizedTest, or @TestFactory method in the current class; analogous to JUnit 4’s @Before. Such methods are inherited – unless they are overridden or superseded (i.e., replaced based on signature only, irrespective of Java’s visibility rules).

@AfterEach

Denotes that the annotated method should be executed after each @Test, @RepeatedTest, @ParameterizedTest, or @TestFactory method in the current class; analogous to JUnit 4’s @After. Such methods are inherited – unless they are overridden or superseded (i.e., replaced based on signature only, irrespective of Java’s visibility rules).

@BeforeAll

Denotes that the annotated method should be executed before all @Test, @RepeatedTest, @ParameterizedTest, and @TestFactory methods in the current class; analogous to JUnit 4’s @BeforeClass. Such methods are inherited – unless they are hidden, overridden, or superseded, (i.e., replaced based on signature only, irrespective of Java’s visibility rules) – and must be static unless the "per-class" test instance lifecycle is used.

@AfterAll

Denotes that the annotated method should be executed after all @Test, @RepeatedTest, @ParameterizedTest, and @TestFactory methods in the current class; analogous to JUnit 4’s @AfterClass. Such methods are inherited – unless they are hidden, overridden, or superseded, (i.e., replaced based on signature only, irrespective of Java’s visibility rules) – and must be static unless the "per-class" test instance lifecycle is used.

@Nested

Denotes that the annotated class is a non-static nested test class. On Java 8 through Java 15, @BeforeAll and @AfterAll methods cannot be used directly in a @Nested test class unless the "per-class" test instance lifecycle is used. Beginning with Java 16, @BeforeAll and @AfterAll methods can be declared as static in a @Nested test class with either test instance lifecycle mode. Such annotations are not inherited.

@Tag

Used to declare tags for filtering tests, either at the class or method level; analogous to test groups in TestNG or Categories in JUnit 4. Such annotations are inherited at the class level but not at the method level.

@Disabled

Used to disable a test class or test method; analogous to JUnit 4’s @Ignore. Such annotations are not inherited.

@Timeout

Used to fail a test, test factory, test template, or lifecycle method if its execution exceeds a given duration. Such annotations are inherited.

@ExtendWith

Used to register extensions declaratively. Such annotations are inherited.

@RegisterExtension

Used to register extensions programmatically via fields. Such fields are inherited unless they are shadowed.

@TempDir

Used to supply a temporary directory via field injection or parameter injection in a lifecycle method or test method; located in the org.junit.jupiter.api.io package.







