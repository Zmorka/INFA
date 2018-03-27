# Systemy operacyjne i programowanie systemowe

1. [Koncepcja systemu operacyjnego, typowa funkcjonalność, realizacje.](#koncepcja-systemu-operacyjnego)
2. [Zarządzanie zasobami, abstrakcje systemowe.](#zarządzanie-zasobami)
3. [Procesy i wątki, wielozadaniowość/wielowątkowość, wielodostęp.](#procesy-i-wątki)
4. [Mechanizmy komunikacji wewnątrzsystemowej.](#mechanizmy-komunikacji)
5. [Zarządzanie zbiorami danych, pliki, systemy plików.](#zarządzanie-zbiorami-danych)
6. [Interfejsy systemowe dla wykonywanego kodu, dla programisty, dla użytkownika.](#interfejsy-systemowe)
7. [Wirtualizacja sprzętu i zasobów systemowych.](#wirtualizacja)
8. [Współczesne koncepcje budowy systemów operacyjnych.](#współczesne-koncepcje)

## Koncepcja systemu operacyjnego

__System operacyjny__ - oprogramowanie, zarządzające systemem komputerowym, tworzące środowisko do uruchamiania i kontroli zadań użytkownika.

W celu uruchamiania i kontroli zadań użytkownika system operacyjny zajmuje się:
- planowaniem oraz przydziałem czasu procesora poszczególnym zadaniom
- kontrolą i przydziałem pamięci operacyjnej dla uruchomionych zadań
- dostarczaniem mechanizmów do synchronizacji zadań i komunikacji pomiędzy zadaniami
- obsługą sprzętu oraz zapewnieniem równolegle wykonywanym zadaniom jednolitego, wolnego od interferencji dostępu do sprzętu.

Dodatkowe przykładowe zadania, którymi może, ale nie musi, zajmować się system operacyjny to
- ustalanie połączeń sieciowych
- zarządzanie plikami.

Większość współczesnych systemów operacyjnych posiada środowiska graficzne ułatwiające komunikacje maszyny z użytkownikiem. 

Budowa:
- jądro systemu wykonujące i kontrolujące zadania
- planisty czasu procesora, ustalającego które zadanie i jak długo będzie wykonywane
- przełącznika zadań, odpowiedzialnego za przełączanie pomiędzy uruchomionymi zadaniami
- powłoka - specjalny program komunikujący użytkownika z systemem operacyjnym
- system plików - sposób ustrukturyzowanego zapisu danych na nośniku.


## Zarządzanie zasobami

- Główne zadania systemu operacyjnego podczas zarządzania zasobami systemu komputerowego
  - tworzenie deskryptora zasobu
  - usuwanie deskryptora zasobu
  - realizacja żądania przydziału
  - zwolnienie i odzyskiwanie zasobu
  
- Zarządzanie zasobami systemu komputerowego
  - przydział zasobów
  - synchronizacja dostępu do zasobów (zapobieganie interferencji)
  - ochrona i autoryzacja dostępu do zasobów
  - odzyskiwanie zasobów
  - rozliczanie - gromadzenie danych o wykorzystaniu zasobów.
  
- Zarządzanie procesem
  - tworzenie i usuwanie procesu
  - wstrzymywanie i przywracanie procesu
  - zapewnienie mechanizmów pozwalających na synchronizację procesów oraz komunikację między procesami.
  
- Zarządzanie pamięcią operacyjną
  - utrzymywanie informacji, która część pamięci jest aktualnie używana i przez kogo
  - decydowania, który proces powinien zostać wczytany do pamięci, jeżeli pamięć jest wolna
  - przydzielanie i zwalnianie pamięci
  
- Zarządzanie plikami
  - tworzenie i kasowanie plików
  - tworzenie i kasowanie katalogów
  - wsparcie dla użytkowników końcowych przy operacjach na plikach
  - mapowanie plików na nośniku danych
  - tworzenie kopii plików
  
- Zarządzanie wejściem/wyjściem - system wejścia/wyjścia składa się z: 
  - systemu buforowania, 
  - interfejsu urządzeń głównych, 
  - sterowników (kontrolerów) dla specyficznych urządzeń.
  
- Zarządzenie nośnikami danych
  - zarządzanie wolną pamięcią
  - alokacją zapisu
  - planowaniem dysku.

## Procesy i wątki

__Proces__ - jedno z najbardziej podstawowych pojęć w informatyce, definiowane jako egzemplarz wykonywanego programu, jednak każdy nowo powstały proces otrzymuje unikalny numer, który go jednoznacznie identyfikuje, tzw. numer PID. W celu wykonania programu system operacyjny przydziela procesowi zasoby (pamięć, czas procesora i inne - szczegółowa lista zasobów znajduje się dalej), ale także może być konieczne współbieżne wykonywanie pewnych fragmentów programu. Aby to zrealizować program może zażądać utworzenia określonej liczby wątków, wykonujących wskazane części programu - o ich współbieżne wykonanie dba system operacyjny (albo sam program, wówczas mówi się o zielonych wątkach). Wątki współdzielą prawie wszystkie zasoby zarezerwowane dla danego procesu, wyjątkiem jest czas procesora, który jest przydzielany indywidualnie każdemu wątkowi.

__Wątek__ - część programu wykonywana współbieżnie w obrębie jednego procesu; w jednym procesie może istnieć wiele wątków. Różnica między zwykłym procesem a wątkiem polega na współdzieleniu przez wszystkie wątki działające w danym procesie przestrzeni adresowej oraz wszystkich innych struktur systemowych (np. listy otwartych plików, gniazd, itp.) - z kolei procesy posiadają niezależne zasoby.

__Wielowątkowość__ - cecha systemu operacyjnego, dzięki której w ramach jednego procesu może wykonywać kilka wątków lub jednostek wykonawczych

__Wielodostęp__ - współdzielenie zasobów komputera pomiędzy kilku użytkowników



## Zarządzanie zbiorami danych

__Plik danych__ - uporządkowany zbiór danych o skończonej długości, posiadający szereg atrybutów i stanowiący dla użytkownika systemu operacyjnego całość. Nazwa pliku nie jest jego częścią, lecz jest przechowywana w systemie plików.

Pliki dzieli się na kilka typów:
- Katalogi - pliki zawierające spis odwołań do innych plików (w tym także do katalogów)
- dowiązania symboliczne - odwołanie do innego pliku; większość operacji na tego typu plikach będzie w rzeczywistości wywoływane na plikach, na które one wskazują
- kolejki FIFO (ang. first in, first out, w skrócie FIFO), gniazda (ang. sockets), strumienie danych oraz inne - realizujące bardziej złożone zadania; nie występują w każdym systemie
- pliki wykonywalne, skrypty (ang. scripts), pliki wsadowe (ang. batch files) - zawierające program do wykonania lub polecenia dla interpretera (często powłoki).

__System plików__ - metoda przechowywania plików, zarządzania plikami, informacjami o tych plikach, tak by dostęp do plików i danych w nich zgromadzonych był łatwy dla użytkownika systemu

Do najbardziej podstawowych wywołań systemowych należą:
- otwieranie pliku (open)
- zamykanie pliku (close)
- tworzenie pliku (create)
- usuwanie pliku (unlink)
- tworzenie katalogu (mkdir)
- usuwanie katalogu (rmdir)
- czytanie z pliku (read)
- pisanie do pliku (write)

Najpopularniejsze systemy:
- FAT 16 (DOS, Windows 98 OSR2)
- FAT 32 (Windows 95 OSR2, Windows 98, Windows ME)
- NTFS (Windows NT, Windows 2000, Windows XP +)
- Ext3 (dystrybucje Linuksa)
- HFS+ (Macintosh OS)

## Mechanizmy komunikacji

Procesy mogą używać różnych sposobów komunikacji, a najpowszechniejsze z nich to
- pliki i blokady - najprostsza i najstarsza forma IPC
- sygnały - w niektórych systemach (jak np. DOS) znane jako przerwania programowe
- semafory 
- potoki nienazwane - znane też jako łącza komunikacyjne
- potoki nazwane - znane też jako nazwane łącza komunikacyjne
- systemy kolejkowe (ang. message queues)
- pamięć dzieloną - znane też jako segmenty pamięci dzielonej (ang. shared memory segments)
- gniazda dziedziny Uniksa (ang. Unix domain sockets)

## Interfejsy systemowe

System operacyjny udostępnia swoje usługi użytkownikom i ich programom poprzez interfejsy programowe.

Funkcje systemowe stanowią interfejs pomiędzy programami a jądrem systemu operacyjnego. Umożliwiają programom korzystanie z usług jądra i sprzętu komputerowego bez naruszania bezpieczeństwa systemu.

Programy systemowe tworzą z kolei interfejs dla użytkowników. W jego skład wchodzą między innymi tekstowe interpretery poleceń oraz programy tworzące interfejs graficzny systemu. Programy systemowe umożliwiają użytkownikom wykonywanie typowych operacji dotyczących manipulowania plikami, przetwarzania ich zawartości, tworzenia i wykonywania programów, komunikacji czy informowania o stanie systemu.

## Wirtualizacja

__Wirtualizacja__ - pojęcie w informatyce, polegające na uruchamianiu wielu systemów operacyjnych na tej samej platformie sprzętowej i systemowej.

Wirtualizacja umożliwia efektywniejsze wykorzystanie istniejących zasobów sprzętowych środowiska informatycznego poprzez dowolne (w ramach możliwości sprzętowych czy programowych oraz założeń projektowych) modyfikowanie cech wirtualizowanych zasobów, dostosowując je do wymagań użytkownika.

__Parawirtualizacja__ - technika wirtualizacji, w której wirtualizowany system operacyjny (Gość - ang. Guest, Partycja - ang. Partition lub Domena - ang. Domain) współpracuje ze środowiskiem operacyjnym komputera w zakresie obsługi tych elementów sprzętowych, których obsługa kolidowałaby z działalnością innych środowisk wirtualizowanych.

__Pełna wirtualizacja__ - technika wirtualizacji, w której wirtualizowany system operacyjny (gość) ma wrażenie, że działa na prawdziwym, fizycznym sprzęcie (komputerze). W rzeczywistości odwołania wirtualizowanego systemu operacyjnego (gościa) do tych elementów fizycznych komputera, które kolidowałyby z działalnością innych środowisk wirtualizowanych lub systemu operacyjnego gospodarza (ang. host), są przechwytywane przez oprogramowanie wirtualizacyjne, a następnie emulowane. Emulacja taka spowalnia pracę wirtualizowanego środowiska, dlatego pożądane jest sprzętowe wspomaganie wirtualizacji.

__Wirtualizacja na poziomie systemu operacyjnego__ - technika wirtualizacji, w której system operacyjny obsługuje kilka odseparowanych od siebie środowisk wirtualnych.

## Współczesne koncepcje

- Jądro
  - Zarządzanie procesami
  - API systemowe
  - Przerwania 
  - Użytkownik standardowy i administrator
  - Zarządzanie pamięcią
    - Stronicowanie - jeden ze sposobów rozwiązania problemu zewnętrznej fragmentacji, polegający na dopuszczeniu nieciągłości rozmieszczenia logicznej przestrzeni adresowej procesu w pamięci fizycznej.
    - Swapping - rozszerzenie dostępnej pamięci za pomocą pamięci zewnętrznej
  - Sterowniki
  - Dyspozytor (ang. scheduler - część systemu operacyjnego odpowiedzialna za przydzielanie czasu procesora w ramach przełączania zadań.
- Interfejs graficzny 
- Wsparcie dla wielu protokołów sieciowych 
- Bezpieczeństwo (firewall, antywirus)
