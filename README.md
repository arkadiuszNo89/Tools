1. SaveCreator:

  Klasa ma za zadanie generowanie pliku tekstowego do zapisu, dodawanie przetworzonej treści do tego pliku lub ładowanie danych z pliku utworzonego wcześniej przez tą klasę.

  Konstruktor przyjmuje tytuł, po którym będzie rozpoznawał plik (notka identyfikacyjna w pliku), nazwę obiektu zapisanego po uprzednim przetworzeniu oraz liczbę linijek, w których zapisany obiekt będzie się zawierał.

  W jednym pliku można dokonać zapisu dla większej ilości obiektów o różnych nazwach i długościach poprzez:

  zmianę obiektu metodą changeObjectType (String typeDescription, int incrementNumber)
  następne dopisanie obiektów do pliku za pomocą trybu ADD_TO_SAVE_FILE
  Mode SAVE służy do nadpisania automatycznie pliku, które wcześniej był zdefiniowany poprzez SAVE_AS.

  Przykład:

  SaveCreator saveC = new SaveCreator("Projekt", "Typ Obiektu", 4);
  
  saveC.act(Mode.SAVE_AS, listaTotal1);
  
  saveC.changeObjectType("Obiekt nr 2", 2);
  
  saveC.act(Mode.ADD_TO_SAVE_FILE, listaTotal2);
  
  ArrayList list = new ArrayList ();
  
  list = saveC.act(Mode.LOAD);
  

2. PaneData

  Klasa przechowująca obiekty klasy Pane oraz obiekty po niej dziedziczące.

  Dodanie obiektu do bazy klasy następuje bezpośrednio po dodaniu Pane'a lub podaniu adresu pliku FXML - dany Pane generuje się przy pomocy FXMLLoadera, a następnie uzupełnia listę

  Dostęp do obiektów uzyskuje się po numeracji lub po nazwie w postaci Stringa, która jest identyfikowana za pomocą mapy

  Przykład:

  PaneData.addPane("border", new BorderPane());
  
  PaneData.addFXML("main", "Sample.fxml");
  
  scene.setRoot(PaneData.get("main"));
  
  scene.setRoot(PaneData.get(0));
  
3. Timer
  
  Klasa podczas tworzenia jej instacji rozpoczyna cykliczny Timer, o częstotliwości nadanej przez nas w parametrze konstruktora. 
  Timer wykonuje metody z listy interfejsów. 
  Do listy nadpisane interfejsy dodajemy sami, w zależności od tego ile i jakie czynności chcemy wykonać co daną jednostkę czasu (addTimeEvent(TimeEvent... events)).
    
  Dotkowo Timer zawiera metody:
  - void play (boolean playState) - uruchamia, bądź zatrzymuje Timer
  - int minutesLongCounter(LocalDate date,  LocalTime time) - przelicznik czasu od momentu użycia metody do momentu podanego poprzez         parametry, w przeliczeniu na minuty.
  - String timeLeft (LocalDate date, LocalTime time) - tak jak wyżej, z tym że zwraca String z czasem rozpisanym na dni, godziny oraz       minuty.
  - double progressCounter(int totalTime, LocalDate date, LocalTime time) - liczy procentowy progres danego wydarzenia w oparciu o           czas początkowy i końcowy. Zwrócona wartość mieści się w przedziale [0,1].
   
 4. InitTools
    
  Zawiera metody do inicjowania obiektów klasy Spinner, DatePicker, TextField.  
     
  Zawiera również:
     
  - <T extends Node> void setVisables(boolean state, T [] arrayOfObjects) - metoda do ustawiania widoczności dla wielu obiektów             jednocześnie
  - void addLabelLine(Pane pane, String style, int fontSize, String... textArray) - metoda dodająca wiele obiektów klasy Label
