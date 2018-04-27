---
title: basic_filebuf — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- fstream/std::basic_filebuf
- fstream/std::basic_filebuf::char_type
- fstream/std::basic_filebuf::int_type
- fstream/std::basic_filebuf::off_type
- fstream/std::basic_filebuf::pos_type
- fstream/std::basic_filebuf::traits_type
- fstream/std::basic_filebuf::close
- fstream/std::basic_filebuf::is_open
- fstream/std::basic_filebuf::open
- fstream/std::basic_filebuf::overflow
- fstream/std::basic_filebuf::pbackfail
- fstream/std::basic_filebuf::seekoff
- fstream/std::basic_filebuf::seekpos
- fstream/std::basic_filebuf::setbuf
- fstream/std::basic_filebuf::Swap
- fstream/std::basic_filebuf::sync
- fstream/std::basic_filebuf::uflow
- fstream/std::basic_filebuf::underflow
dev_langs:
- C++
helpviewer_keywords:
- std::basic_filebuf [C++]
- std::basic_filebuf [C++], char_type
- std::basic_filebuf [C++], int_type
- std::basic_filebuf [C++], off_type
- std::basic_filebuf [C++], pos_type
- std::basic_filebuf [C++], traits_type
- std::basic_filebuf [C++], close
- std::basic_filebuf [C++], is_open
- std::basic_filebuf [C++], open
- std::basic_filebuf [C++], overflow
- std::basic_filebuf [C++], pbackfail
- std::basic_filebuf [C++], seekoff
- std::basic_filebuf [C++], seekpos
- std::basic_filebuf [C++], setbuf
- std::basic_filebuf [C++], Swap
- std::basic_filebuf [C++], sync
- std::basic_filebuf [C++], uflow
- std::basic_filebuf [C++], underflow
ms.assetid: 3196ba5c-bf38-41bd-9a95-70323ddfca1a
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f39b72fd6ef7d734539a9d0677aeb60ca74bec41
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="basicfilebuf-class"></a>basic_filebuf — Klasa

W tym artykule opisano buforu strumienia, który kontroluje przekazywania elementów typu `Elem`, którego cech znaków są określane przez klasę `Tr`, do i z sekwencję elementy przechowywane w pliku zewnętrznym.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_filebuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Parametry

`Elem` Podstawowy element buforu plików.

`Tr` Cechy podstawowy element pliku buforu (zazwyczaj `char_traits` <  `Elem`>).

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje buforu strumienia, który kontroluje przekazywania elementów typu `Elem`, którego cech znaków są określane przez klasę `Tr`, do i z sekwencję elementy przechowywane w pliku zewnętrznym.

> [!NOTE]
> Obiekty typu `basic_filebuf` są tworzone z buforu wewnętrznego typu `char *` niezależnie od tego `char_type` określonej przez parametr typu `Elem`. Oznacza to, że ciąg Unicode (zawierający `wchar_t` znaków) zostaną skonwertowane do ciągu ANSI (zawierający `char` znaków) zanim zostaną zapisane do wewnętrznego buforu. Do przechowywania ciągów Unicode w buforze, Utwórz bufor nowego typu `wchar_t` i ustaw ją przy użyciu [basic_streambuf::pubsetbuf](../standard-library/basic-streambuf-class.md#pubsetbuf) `()` metody. Aby zapoznać się przykładem, który demonstruje tego zachowania, zobacz poniżej.

Obiekt klasy `basic_filebuf` <  `Elem`, `Tr`> przechowuje wskaźnika pliku, który wyznacza `FILE` obiekt, który kontroluje strumienia skojarzonego z otwartego pliku. Przechowuje także wskaźniki do dwa aspekty konwersji plików do użycia przez funkcje chroniony element członkowski [przepełnienie](#overflow) i [niedopełnienie](#underflow). Aby uzyskać więcej informacji, zobacz [basic_filebuf::open](#open).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak wymusić typu obiektu `basic_filebuf<wchar_t>` do przechowywania znaków Unicode w swoim buforze wewnętrzny przez wywołanie metody `pubsetbuf()` metody.

```cpp
// unicode_basic_filebuf.cpp
// compile with: /EHsc

#include <iostream>
#include <string>
#include <fstream>
#include <iomanip>
#include <memory.h>
#include <string.h>

#define IBUFSIZE 16

using namespace std;

void hexdump(const string& filename);

int main()
{
    wchar_t* wszHello = L"Hello World";
    wchar_t wBuffer[128];

    basic_filebuf<wchar_t> wOutFile;

    // Open a file, wcHello.txt, then write to it, then dump the
    // file's contents in hex
    wOutFile.open("wcHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wcHello.txt\n";
        return -1;
    }
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "Hex Dump of wcHello.txt - note that output is ANSI chars:\n";
    hexdump(string("wcHello.txt"));

    // Open a file, wwHello.txt, then set the internal buffer of
    // the basic_filebuf object to be of type wchar_t, then write
    // to the file and dump the file's contents in hex
    wOutFile.open("wwHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wwHello.txt\n";
        return -1;
    }
    wOutFile.pubsetbuf(wBuffer, (streamsize)128);
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "\nHex Dump of wwHello.txt - note that output is wchar_t chars:\n";
    hexdump(string("wwHello.txt"));

    return 0;
}

// dump contents of filename to stdout in hex
void hexdump(const string& filename)
{
    fstream ifile(filename.c_str(),
        ios_base::in | ios_base::binary);
    char *ibuff = new char[IBUFSIZE];
    char *obuff = new char[(IBUFSIZE*2)+1];
    int i;

    if(!ifile.is_open())
    {
        cout << "Cannot Open " << filename.c_str()
             << " for reading\n";
        return;
    }
    if(!ibuff || !obuff)
    {
        cout << "Cannot Allocate buffers\n";
        ifile.close();
        return;
    }

    while(!ifile.eof())
    {
        memset(obuff,0,(IBUFSIZE*2)+1);
        memset(ibuff,0,IBUFSIZE);
        ifile.read(ibuff,IBUFSIZE);

        // corner case where file is exactly a multiple of
        // 16 bytes in length
        if(ibuff[0] == 0 && ifile.eof())
            break;

        for(i = 0; i < IBUFSIZE; i++)
        {
            if(ibuff[i] >= ' ')
                obuff[i] = ibuff[i];
            else
                obuff[i] = '.';

            cout << setfill('0') << setw(2) << hex
                 << (int)ibuff[i] << ' ';
        }
        cout << "  " << obuff << endl;
    }
    ifile.close();
}
```

```Output
Hex Dump of wcHello.txt - note that output is ANSI chars:
48 65 6c 6c 6f 20 57 6f 72 6c 64 00 00 00 00 00   Hello World.....

Hex Dump of wwHello.txt - note that output is wchar_t chars:
48 00 65 00 6c 00 6c 00 6f 00 20 00 57 00 6f 00   H.e.l.l.o. .W.o.
72 00 6c 00 64 00 00 00 00 00 00 00 00 00 00 00   r.l.d...........
```

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_filebuf](#basic_filebuf)|Tworzy obiekt typu `basic_filebuf`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Kojarzy nazwę typu z `Elem` parametru szablonu.|
|[int_type](#int_type)|Sprawia, że ten typ w `basic_filebuf`jego odpowiednikiem typu o takiej samej nazwie w zakresie `Tr` zakresu.|
|[off_type](#off_type)|Sprawia, że ten typ w `basic_filebuf`jego odpowiednikiem typu o takiej samej nazwie w zakresie `Tr` zakresu.|
|[pos_type](#pos_type)|Sprawia, że ten typ w `basic_filebuf`jego odpowiednikiem typu o takiej samej nazwie w zakresie `Tr` zakresu.|
|[traits_type](#traits_type)|Kojarzy nazwę typu z `Tr` parametru szablonu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[close](#close)|Zamyka plik.|
|[is_open](#is_open)|Wskazuje, czy plik jest otwarty.|
|[open](#open)|Otwiera plik.|
|[overflow](#overflow)|Chronione funkcji wirtualnej można wywołać po wstawieniu nowego znaku w buforze pełna.|
|[pbackfail](#pbackfail)|Funkcja chroniony element członkowski wirtualnego próbuje ponownie poddane elementu wejściowego strumienia, a następnie wprowadź go bieżącego elementu (wskazywana przez wskaźnik następnej).|
|[seekoff](#seekoff)|Funkcja chronionego członka wirtualnego próbuje zmienić bieżącego położenia dla strumieni kontrolowane.|
|[seekpos](#seekpos)|Funkcja chronionego członka wirtualnego próbuje zmienić bieżącego położenia dla strumieni kontrolowane.|
|[setbuf](#setbuf)|Funkcja chroniony element członkowski wirtualnego wykonuje określonego operację do każdego strumienia pochodnej buforu.|
|[Swap](#swap)|Zamienia zawartość tego `basic_filebuf` zawartości dotyczącej dostępnego `basic_filebuf` parametru.|
|[sync](#sync)|Funkcja chroniony, wirtualny próbuje synchronizować kontrolowane strumieni wszystkie skojarzone strumieni zewnętrznych.|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|Chronione funkcji wirtualnych można wyodrębnić bieżącego elementu ze strumienia wejściowego.|
|[underflow](#underflow)|Chronione funkcji wirtualnych można wyodrębnić bieżącego elementu ze strumienia wejściowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<fstream — >

**Namespace:** Standard

## <a name="basic_filebuf"></a>  basic_filebuf::basic_filebuf

Tworzy obiekt typu `basic_filebuf`.

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje wskaźnika o wartości null w wszystkie wskaźniki kontrolowanie buforu wejściowego i buforu wyjściowego. Przechowuje także wskaźnika o wartości null wskaźnika pliku.

Drugi Konstruktor inicjuje obiekt z zawartością `right`, traktowane jako odwołanie do r-wartości.

## <a name="char_type"></a>  basic_filebuf::char_type

Kojarzy nazwę typu z **elementu** parametru szablonu.

```cpp
typedef Elem char_type;
```

## <a name="close"></a>  basic_filebuf::Close

Zamyka plik.

```cpp
basic_filebuf<Elem, Tr> *close();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zwraca wskaźnika o wartości null, jeśli wskaźnika o wartości null wskaźnika pliku.

### <a name="remarks"></a>Uwagi

**Zamknij** wywołania `fclose`( **fp**). Jeśli ta funkcja zwróci wartość niezerową, funkcja zwraca wskaźnika o wartości null. W przeciwnym razie zwraca **to** aby wskazać, że plik został zamknięty pomyślnie.

Dla strumienia szerokości, jeśli wystąpiły wstawienia wszelkie ponieważ strumień został otwarty lub od czasu ostatniego wywołania `streampos`, wywołania funkcji [przepełnienie](#overflow). Również wstawia żadnych sekwencji potrzebne do przywrócenia stanu początkowego konwersji przy użyciu pliku aspekt konwersji **fac** do wywołania **fac.unshift** zgodnie z potrzebami. Każdy element **bajtów** typu `char` w związku z tym tworzone są zapisywane do strumienia skojarzone wskazywany przez wskaźnika pliku **fp** funkcję Jeśli kolejnych wywołań w postaci `fputc`( **bajtów**, **fp**). Jeśli wywołanie **fac.unshift** lub dowolnego zapis kończy się niepowodzeniem, funkcja nie powiedzie się.

### <a name="example"></a>Przykład

Poniższy przykład przyjmuje dwa pliki w bieżącym katalogu: basic_filebuf_close.txt (zawartość "testuje") i iotest.txt (zawartość jest "SSS").

```cpp
// basic_filebuf_close.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main() {
   using namespace std;
   ifstream file;
   basic_ifstream <wchar_t> wfile;
   char c;
   // Open and close with a basic_filebuf
   file.rdbuf()->open( "basic_filebuf_close.txt", ios::in );
   file >> c;
   cout << c << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "iotest.txt" );
   file >> c;
   cout << c << endl;
   file.close( );

   // open a file with a wide character name
   wfile.open( L"iotest.txt" );

   // Open and close a nonexistent with a basic_filebuf
   file.rdbuf()->open( "ziotest.txt", ios::in );
   cout << file.fail() << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "ziotest.txt" );
   cout << file.fail() << endl;
   file.close( );
}
```

```Output
t
s
0
1
```

## <a name="int_type"></a>  basic_filebuf::int_type

Sprawia, że ten typ w zakresie basic_filebuf — jego odpowiednikiem typu o takiej samej nazwie w **Tr** zakresu.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="is_open"></a>  basic_filebuf::is_open

Wskazuje, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wskaźnika pliku nie jest wskaźnika o wartości null.

### <a name="example"></a>Przykład

```cpp
// basic_filebuf_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   cout << boolalpha << file.rdbuf( )->is_open( ) << endl;

   file.open( "basic_filebuf_is_open.cpp" );
   cout << file.rdbuf( )->is_open( ) << endl;
}
```

```Output
false
true
```

## <a name="off_type"></a>  basic_filebuf::off_type

Sprawia, że ten typ w zakresie basic_filebuf — jego odpowiednikiem typu o takiej samej nazwie w **Tr** zakresu.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="open"></a>  basic_filebuf::Open

Otwiera plik.

```cpp
basic_filebuf<Elem, Tr> *open(
    const char* _Filename,
    ios_base::openmode _Mode,
    int _Prot = (int)ios_base::_Openprot);

basic_filebuf<Elem, Tr> *open(
    const char* _Filename,
    ios_base::openmode _Mode);

basic_filebuf<Elem, Tr> *open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode,
    int _Prot = (int)ios_base::_Openprot);

basic_filebuf<Elem, Tr> *open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>Parametry

`_Filename` Nazwa pliku, aby otworzyć.

`_Mode` Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

`_Prot` Domyślny plik otwierania ochrony odpowiednikiem `shflag` parametru w [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="return-value"></a>Wartość zwracana

Jeśli wskaźnika pliku wskaźnika o wartości null, funkcja zwraca wskaźnika o wartości null. W przeciwnym razie zwraca **to**.

### <a name="remarks"></a>Uwagi

Funkcja członkowska otwiera plik o nazwie pliku *filename*, wywołując [fopen —](../c-runtime-library/reference/fopen-wfopen.md)( *filename*, **strmode**). **strmode** jest określana na podstawie **trybu &**~ ( [uj](../standard-library/ios-base-class.md#openmode) & &#124; [binary](../standard-library/ios-base-class.md#openmode)):

- **ios_base::in** staje się **"r"** (Otwórz istniejący plik do odczytu).

- [ios_base::Out](../standard-library/ios-base-class.md#fmtflags) lub **ios_base::out &#124; ios_base::trunc** staje się **"w"** (obcięcia istniejący plik lub utwórz do zapisu).

- **ios_base::Out &#124; aplikacji** staje się **""** (Otwórz istniejący plik dołączania zapisy wszystkie).

- **ios_base::in &#124; ios_base::out** staje się **"r +"** (Otwórz istniejący plik do odczytu i zapisu).

- **ios_base::in &#124; ios_base::out &#124; ios_base::trunc** staje się **"w +"** (obcięcia istniejący plik lub utwórz do odczytywania i zapisywania).

- **ios_base::in &#124; ios_base::out &#124; ios_base::app** staje się **"+"** (Otwórz istniejący plik do odczytu i dołączania zapisy wszystkie).

Jeśli **trybu & ios_base::binary** jest różna od zera, dołącza funkcji **b** do **strmode** można otworzyć strumienia binarnego zamiast strumienia tekstu. Następnie zapisuje wartość zwrócona przez `fopen` wskaźnika pliku **fp**. Jeśli **trybu & ios_base::ate** jest różna od zera i wskaźnika pliku nie jest wskaźnika o wartości null, wywołania funkcji `fseek`( **fp**, 0, `SEEK_END`) do pozycji w strumieniu na końcu pliku. Jeśli tej operacji pozycjonowania zakończy się niepowodzeniem, wywołania funkcji [zamknąć](#close)( **fp**) i przechowuje wskaźnika o wartości null wskaźnika pliku.

Jeśli wskaźnika pliku nie jest wskaźnika o wartości null, funkcja określa aspekt konwersji plików: `use_facet` <  `codecvt` <  **elementu**, `char`, **traits_type::** [ state_type](../standard-library/char-traits-struct.md#state_type)>> ( [getloc](../standard-library/basic-streambuf-class.md#getloc)), do użycia przez [niedopełnienie](#underflow) i [przepełnienie](#overflow).

Jeśli wskaźnika pliku wskaźnika o wartości null, funkcja zwraca wskaźnika o wartości null. W przeciwnym razie zwraca **to**.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](#close) na przykład, który używa **Otwórz**.

## <a name="op_eq"></a>  basic_filebuf::operator =

Przypisz zawartość tego obiektu buforu strumienia. Jest to przypisania przenoszenia, obejmujące r-wartości nie pozostawione kopii.

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>Parametry

`right` Odwołania do r-wartości do [basic_filebuf —](../standard-library/basic-filebuf-class.md) obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca * to.

### <a name="remarks"></a>Uwagi

Operator członkowski zastępuje zawartość obiektu przy użyciu zawartości `right`, traktowane jako odwołanie do r-wartości. Aby uzyskać więcej informacji, zobacz [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="overflow"></a>  basic_filebuf::Overflow

Wywołuje się po wstawieniu nowego znaku w buforze pełna.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parametry

`_Meta` Znak do wstawienia w buforze lub **traits_type::eof**.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść, zwraca **traits_type::eof**. W przeciwnym razie zwraca **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Uwagi

Jeśli _ * Meta ***! = traits_type::**[eof](../standard-library/char-traits-struct.md#eof), funkcja chroniony element członkowski wirtualnego usiłują wstawienie elementu **ch = traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type) (\_ *Meta*) do buforu wyjściowego. Go to zrobić na różne sposoby:

- Jeśli pozycja zapisu jest dostępny, można przechowywać elementu w miejscu zapisu i zwiększyć wskaźnik następnej buforu danych wyjściowych.

- Go można udostępnić pozycję zapisu przydzielając nowej lub dodatkowej pamięci masowej dla buforu danych wyjściowych.

- Umożliwia on konwertowanie żadnych oczekujących danych wyjściowych w buforze danych wyjściowych, a następnie **ch**, przy użyciu pliku aspekt konwersji **fac** do wywołania **fac.out** zgodnie z potrzebami. Każdy element `ch` typu *char* w związku z tym tworzone są zapisywane do strumienia skojarzone wskazywany przez wskaźnika pliku **fp** funkcję Jeśli kolejnych wywołań w postaci `fputc`( **ch**, **fp**). W przypadku niepowodzenia konwersji ani zapisu funkcji nie powiedzie się.

## <a name="pbackfail"></a>  basic_filebuf::pbackfail

Próbuje ponownie poddane elementu wejściowego strumienia, a następnie wprowadź go bieżącego elementu (wskazywana przez wskaźnik następnej).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parametry

`_Meta` Znak do wstawienia w buforze, lub **traits_type::eof**.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść, zwraca **traits_type::eof**. W przeciwnym razie zwraca **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego umieszcza ponownie element buforu wejściowego i czyni go po bieżącego elementu (wskazywana przez wskaźnik następnej). Jeśli _ *Meta* **== traits_type::**[eof](../standard-library/char-traits-struct.md#eof), elementu do usunięcia jest już w strumieniu przed bieżącego elementu. W przeciwnym razie ten element został zastąpiony przez **ch = traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*). Funkcja można odłożyć element na różne sposoby:

- Jeśli pozycja putback jest dostępne, a element przechowywane porównuje równa **ch**, jego zmniejszanie wskaźnik następnej dla buforu wejściowego.

- Jeśli funkcja mogą wysyłać `putback` miejsce dostępne, można to zrobić, ustawienia wskaźnika dalej, aby wskazywały na pozycji i przechowywać **ch** w tej lokalizacji.

- Jeśli funkcja można wypchnąć ponownie element na strumień wejściowy, go to zrobić, takich jak wywołując `ungetc` dla elementu typu `char`.

## <a name="pos_type"></a>  basic_filebuf::pos_type

Sprawia, że ten typ w zakresie basic_filebuf — jego odpowiednikiem typu o takiej samej nazwie w **Tr** zakresu.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_filebuf::seekoff

Próbuje zmienić bieżącego położenia dla strumieni kontrolowane.

```cpp
virtual pos_type seekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

`_Off` Położenie do wyszukania dla względem `_Way`.

`_Way` Punkt początkowy dla operacji przesunięcia. Zobacz [seekdir](../standard-library/ios-base-class.md#seekdir) prawidłowych wartości.

`_Which` Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.

### <a name="return-value"></a>Wartość zwracana

Zwraca nowego położenia lub nieprawidłowy strumień pozycji.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego usiłują alter dla strumieni kontrolowane bieżącej pozycji. Dla obiekt klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, pozycji w strumieniu może być reprezentowany przez obiekt typu `fpos_t`, która przechowuje przesunięcie i konieczne jest żadnych informacji o stanie przeanalizować szeroki strumienia. Przesunięcia zero oznacza pierwszego elementu obiektu strumienia. (Obiekt typu [pos_type](../standard-library/basic-streambuf-class.md#pos_type) przechowuje co najmniej `fpos_t` obiektu.)

Plik otwarty do odczytu i zapisu strumienie wejściowe i wyjściowe są pozycjonowane wspólnie. Aby przełączyć między Wstawianie i wyodrębnianie, należy wywołać albo [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff) lub [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos). Wywołuje się `pubseekoff` (i dlatego do `seekoff`) mają różne ograniczenia dotyczące [strumienie tekstu](../c-runtime-library/text-and-binary-streams.md), [strumienie binarne](../c-runtime-library/text-and-binary-streams.md), i [szerokie strumienie](../c-runtime-library/byte-and-wide-streams.md).

Jeśli wskaźnika pliku **fp** wskaźnik null, funkcja kończy się niepowodzeniem. W przeciwnym razie usiłują zmiany wywołując pozycji w strumieniu `fseek`( **fp**, `_Off`, `_Way`). Jeśli ta funkcja zakończy się powodzeniem i wynikowy pozycji **fposn** można ustalić wywołując `fgetpos`( **fp**, **& fposn**), funkcja zakończy się pomyślnie. Jeśli funkcja zakończy się powodzeniem, funkcja zwraca wartość typu **pos_type** zawierający **fposn**. W przeciwnym razie zwraca wartość pozycji nieprawidłowy strumień.

## <a name="seekpos"></a>  basic_filebuf::seekpos

Próbuje zmienić bieżącego położenia dla strumieni kontrolowane.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

`_Sp` Położenie do wyszukania dla.

`_Which` Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.

### <a name="return-value"></a>Wartość zwracana

Jeśli wskaźnika pliku **fp** wskaźnik null, funkcja kończy się niepowodzeniem. W przeciwnym razie usiłują zmiany wywołując pozycji w strumieniu `fsetpos`( **fp**, **& fposn**), gdzie **fposn** jest `fpos_t` obiektu przechowywanego w `pos`. Jeśli ta funkcja zakończy się powodzeniem, funkcja zwraca `pos`. W przeciwnym razie zwraca wartość pozycji nieprawidłowy strumień. Aby ustalić, czy pozycja strumienia jest nieprawidłowa, porównanie wartości zwracanych z `pos_type(off_type(-1))`.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego usiłują alter dla strumieni kontrolowane bieżącej pozycji. Dla obiekt klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md) \< **elementu**, **Tr**>, pozycji w strumieniu może być reprezentowany przez obiekt typu `fpos_t`, której są przechowywane Przesunięcie i żadnych informacji o stanie potrzebnych do analizy strumienia szerokości. Przesunięcia zero oznacza pierwszego elementu obiektu strumienia. (Obiekt typu `pos_type` przechowuje co najmniej `fpos_t` obiektu.)

Plik otwarty do odczytu i zapisu strumienie wejściowe i wyjściowe są pozycjonowane wspólnie. Aby przełączyć między Wstawianie i wyodrębnianie, należy wywołać albo [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff) lub [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos). Wywołuje się `pubseekoff` (i dlatego aby `seekoff`) mają różne ograniczenia strumienie tekstu, strumienie binarne i szerokie strumienie.

Dla strumienia szerokości, jeśli wystąpiły wstawienia wszelkie ponieważ strumień został otwarty lub od czasu ostatniego wywołania `streampos`, wywołania funkcji [przepełnienie](#overflow). Również wstawia żadnych sekwencji potrzebne do przywrócenia stanu początkowego konwersji przy użyciu pliku aspekt konwersji **fac** do wywołania **fac** `.unshift` zgodnie z potrzebami. Każdy element **bajtów** typu `char` w związku z tym tworzone są zapisywane do strumienia skojarzone wskazywany przez wskaźnika pliku **fp** funkcję Jeśli kolejnych wywołań w postaci `fputc`( **bajtów**, **fp**). Jeśli wywołanie **fac.unshift** lub dowolnego zapis kończy się niepowodzeniem, funkcja nie powiedzie się.

## <a name="setbuf"></a>  basic_filebuf::setbuf

Wykonuje określonego operację do każdego strumienia pochodnej buforu.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

`_Buffer` Wskaźnik do buforu.

`count` Rozmiar buforu.

### <a name="return-value"></a>Wartość zwracana

Funkcja chroniony element członkowski zwraca zero, jeśli wskaźnika pliku `fp` jest wskaźnika o wartości null.

### <a name="remarks"></a>Uwagi

`setbuf` wywołania `setvbuf`( **fp**, ( `char` \*) `_Buffer`, `_IOFBF`, `count` \* `sizeof` ( **elementu**)) do zaoferowania tablicy z `count` elementów, rozpoczynając od _ *buforu* jako bufor dla tego strumienia. Jeśli ta funkcja zwróci wartość niezerową, funkcja zwraca wskaźnika o wartości null. W przeciwnym razie zwraca **to** Powodzenie sygnału.

## <a name="swap"></a>  basic_filebuf::swap

Zamienia zawartość tych `basic_filebuf` dla zawartości określonego `basic_filebuf`.

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>Parametry

`right` `lvalue` Odwołania do innego `basic_filebuf`.

## <a name="sync"></a>  basic_filebuf::Sync

Próbuje synchronizować kontrolowane strumieni wszystkie skojarzone strumieni zewnętrznych.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca zero, jeśli wskaźnika pliku **fp** jest wskaźnika o wartości null. W przeciwnym razie zwraca zero tylko wtedy, gdy wywołuje zarówno do [przepełnienie](#overflow) i `fflush`( **fp**) uda się opróżnianie wszelkie oczekujące dane wyjściowe do strumienia.

## <a name="traits_type"></a>  basic_filebuf::traits_type

Kojarzy nazwę typu z **Tr** parametru szablonu.

```cpp
typedef Tr traits_type;
```

## <a name="underflow"></a>  basic_filebuf::underflow

Wyodrębnia bieżącego elementu ze strumienia wejściowego.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść, zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). W przeciwnym razie zwraca **ch**konwersji, zgodnie z opisem w sekcji uwag.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego usiłują wyodrębnić bieżącego elementu **ch** wejściowego strumienia i zwracać element jako **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)() **ch**). Go to zrobić na różne sposoby:

- Jeśli pozycja odczytu jest dostępny, przyjmuje **ch** jako element przechowywane w pozycji odczytu i przesuwa wskaźnik następnej dla buforu wejściowego.

- Można odczytać co najmniej jeden element typu `char`, tak, jakby w kolejnych wywołaniach formularza `fgetc`(**fp**) i przekonwertować je na element **ch** typu **elementu**przy użyciu fac aspektu konwersji plików do wywołania **fac.in** zgodnie z potrzebami. W przypadku niepowodzenia odczytu ani konwersji funkcji nie powiedzie się.

## <a name="see-also"></a>Zobacz także

[\<fstream>](../standard-library/fstream.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
