# Architektura Komputerów

1. [Struktura i organizacja typowego systemu komputerowego.](#struktura-i-organizacja)
2. [Budowa i działanie typowego procesora ogólnego przeznaczenia.](#budowa-i-działanie-procesora)
3. [Wykonywanie rozkazów przez procesor(y), przerwania, wyjątki.](#wykonywanie-rozkazów-przez-procesor)
4. [Dane i ich przetwarzanie w systemie komputerowym.](#dane-i-ich-przetwarzanie)
5. [Koncepcja „konwencjonalnej maszyny”, język maszynowy, asembler.](#koncepcja-konwencjonalnej-maszyny)
6. [Połączenia wewnątrz- i zewnątrz-systemowe, urządzenia wejścia/wyjścia.](#połączenia-systemowe)
7. [Realizacja przetwarzania równoległego w systemach komputerowych.](#realizacja-przetwarzania-równoległego)
8. [Optymalizacja wydajności procesora(ów) i systemu komputerowego.](#optymalizacja-wydajności-procesora)

## Struktura i organizacja

![Architektura](./Images/architecture.png)

## Budowa i działanie procesora

- układ sterowania i synchronizacji, który kontroluje pracę procesora i wytwarza sygnały potrzebne do sterowania niektórymi elementami komputera.
- arytmometr, czyli układ, który wykonuje operacje arytmetyczne i logiczne (niektóre procesory mają kilka arytmometrów).
- rejestry, służące do przechowywania tymczasowych wyników obliczeń, adresów lokacji w pamięci operacyjnej
- wbudowana pamięć podręczna cache, która działa podobnie do zewnętrznej pamięci RAM. Zapewnia ona, że procesor nie jest zmuszony czekać na dane potrzebne mu do pracy.
- spółczesne technologie 
  - Architektura 64 bitowa
  - Wielordzeniowość 
  - Wielowątkowość (Dwa wątki na jeden rdzeń fizyczny) 

## Wykonywanie rozkazów przez procesor

__Rozkaz__ - w informatyce i programowaniu to pojedyncza operacja centralnej jednostki obliczeniowej określona przez zestaw rozkazów jej modelu programowego. Jest ona przekazywana do procesora, który ją dekoduje, a następnie wykonuje, po czym zapisuje wartość wynikową w określonym miejscu lub ustawia flagę błędu, jeżeli wystąpił on podczas przetwarzania.

__Wyjątek__ - jest to dowolne zdarzenie, które przerywa normalny tok obliczeń procesora i wymusza wykonanie określonego zbioru instrukcji w trybie uprzywilejowanym. Najogólniej można je podzielić na dwie grupy: synchroniczne i asynchroniczne. Synchroniczne są generowane przez tzw. zdarzenia wewnętrzne jak np. efekt wykonania jakiejś instrukcji procesora. Przykładami mogą być dzielenie przez zero lub niepoprawny odczyt z pamięci.

__Przerwanie__ - to tzw. wyjątki asynchroniczne i nie są powiązane z instrukcjami wykonywanymi przez procesor. Ich źródłem są wszelkie zdarzenia zewnętrzne, czyli odnoszą się do różnych sygnałów generowanych przez sprzęt. Przykładami mogą być wciśnięcie przycisku reset na płycie głównej lub urządzenie komunikacyjne, które właśnie otrzymało pakiet z danymi.

## Dane i ich przetwarzanie

__Pamięć masowa__ - pamięć trwała, która umożliwia przechowywanie dużych ilości danych przez długi czas. W odróżnieniu od pamięci operacyjnej, nie pozwala na adresowanie pojedynczych bajtów, a jej czas dostępu jest wielokrotnie dłuższy

__Bit__ -  najmniejsza ilość informacji potrzebna do określenia, który z dwóch równie prawdopodobnych   stanów   przyjął   układ.  Jednostka logiczna. Jest to również najmniejsza jednostka informacji używana w odniesieniu do sprzętu komputerowego a oznaczana jest za pomocą b.

__Bajt__ -  najmniejsza adresowalna jednostka informacji pamięci komputerowej, składająca się z bitów.  W praktyce przyjmuje się, że jeden bajt to 8 bitów.

## Koncepcja konwencjonalnej maszyny

__Język maszynowy__, __kod maszynowy__ - zestaw rozkazów procesora, w którym zapis programu wyrażony jest w postaci liczb binarnych stanowiących rozkazy oraz ich argumenty. Kod maszynowy może być generowany w procesie kompilacji (w przypadku języków wysokiego poziomu) lub asemblacji (w przypadku języków niskiego poziomu)

__Asembler__ - program tworzący kod maszynowy na podstawie kodu źródłowego (tzw. asemblacja) wykonanego w niskopoziomowym języku programowania bazującym na podstawowych operacjach procesora zwanym językiem asemblera, popularnie nazywanym również asemblerem.

__Języki asemblera__ - rodzina języków programowania niskiego poziomu, których jedno polecenie odpowiada zasadniczo jednemu rozkazowi procesora.

## Połączenia systemowe

__Urządzenie wejścia-wyjścia__ - urządzenie do komunikacji systemu komputerowego z jego użytkownikiem lub innym systemem przetwarzania danych.

- urządzenia wejścia to: 
  - klawiatura, 
  - mysz, 
  - mikrofon, 
  - czytnik linii papilarnych
- urządzenia wyjścia to: 
  - monitor, 
  - drukarka, 
  - głośniki, 
  - słuchawki
- urządzenia wejścia i wyjścia to: 
  - karta sieciowa, 
  - modem, 
  - ekran dotykowy

## Realizacja przetwarzania równoległego

__Obliczenia równoległe__ - forma wykonywania obliczeń, w której wiele instrukcji jest wykonywanych jednocześnie. Taka forma przetwarzania danych była wykorzystywana przez wiele lat, głównie przy wykorzystaniu superkomputerów, a szczególne zainteresowanie zyskała w ostatnich latach, z uwagi na fizyczne ograniczenia uniemożliwiające dalsze zwiększanie częstotliwości taktowania procesorów. Obliczenia równoległe stały się dominującym wzorcem w architekturze komputerowej, głównie za sprawą upowszechnienia procesorów wielordzeniowych.

Ze względu na skalę można wyróżnić obliczenia równoległe na poziomie: bitów, instrukcji, danych i zadań

Ze względu na poziom, na którym sprzęt wspomaga operacje równoległe, można wyróżnić komputery:
jednoprocesorowe wielordzeniowe (zawierające jeden procesor wielordzeniowy)
symetryczne wieloprocesorowe (zawierające kilka identycznych, równorzędnych procesorów)
systemy składające się z wielu maszyn: klastry, systemy MPP, gridy.

Do prowadzenia obliczeń równoległych, oprócz sprzętu, konieczne są również odpowiednie algorytmy nazywane równoległymi. Są one trudniejsze w implementacji niż sekwencyjne, ponieważ współbieżność wprowadza dodatkowe możliwości popełnienia błędu. Powstają również dodatkowe problemy w uzyskaniu wysokiej wydajności z powodu dodatkowych nakładów na komunikację i konieczność synchronizacji obliczeń.

## Optymalizacja wydajności procesora

- Dynamiczna częstotliwość taktowania rdzeni 
- Wielowątkowość (hiper-threading, simultaneous-multithreading)
- Pamięć podręczna cache (znacznie szybsza niż RAM)
- Spekulatywne wykonywanie instrukcji 
