---
title: Klasa CStdioFile
ms.date: 11/04/2016
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
helpviewer_keywords:
- CStdioFile [MFC], CStdioFile
- CStdioFile [MFC], Open
- CStdioFile [MFC], ReadString
- CStdioFile [MFC], Seek
- CStdioFile [MFC], WriteString
- CStdioFile [MFC], m_pStream
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
ms.openlocfilehash: dd1a13e7cef066350f8409782b0efeba11b9d11e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456215"
---
# <a name="cstdiofile-class"></a>Klasa CStdioFile

Reprezentuje plik strumienia środowiska uruchomieniowego C otwartego przy użyciu funkcji wykonawczej [fopen —](../../c-runtime-library/reference/fopen-wfopen.md).

## <a name="syntax"></a>Składnia

```
class CStdioFile : public CFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|Konstruuje `CStdioFile` obiektu ze wskaźnikiem pliku lub ścieżki.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStdioFile::Open](#open)|Przeciążone. Otwórz jest przeznaczony do użytku przy użyciu domyślnego `CStdioFile` konstruktora (zastępuje [CFile::Open](../../mfc/reference/cfile-class.md#open)).|
|[CStdioFile::ReadString](#readstring)|Odczytuje pojedynczy wiersz tekstu.|
|[CStdioFile::Seek](#seek)|Ustawia bieżący wskaźnik pliku.|
|[CStdioFile::WriteString](#writestring)|Zapisuje pojedynczy wiersz tekstu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|Zawiera wskaźnik do otwartego pliku.|

## <a name="remarks"></a>Uwagi

Pliki Stream są buforowane i mogą być otwierane w trybie tekstowym (ustawienie domyślne) lub w trybie binarnym.

Tryb tekstu zapewnia specjalnego przetwarzania dla par wysuwu wiersza powrotu karetki. Podczas wpisywania nowy wiersz znaków (0x0A) do trybu tekstowego `CStdioFile` object, pary bajtów (0x0D, 0x0A) są wysyłane do pliku. Po przeczytaniu, pary bajtów (0x0D, 0x0A) jest tłumaczona na 0x0A jednobajtowych.

[CFile](../../mfc/reference/cfile-class.md) funkcje [zduplikowane](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), i [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) nie są obsługiwane w przypadku `CStdioFile`.

Jeśli chcesz wywołać te funkcje w `CStdioFile`, otrzymasz [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Aby uzyskać więcej informacji na temat korzystania z `CStdioFile`, zobacz artykuły [pliki w MFC](../../mfc/files-in-mfc.md) i [Obsługa plików](../../c-runtime-library/file-handling.md) w *odwołanie do biblioteki wykonawczej*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="cstdiofile"></a>  CStdioFile::CStdioFile

Tworzy i inicjuje `CStdioFile` obiektu.

```
CStdioFile();
CStdioFile(CAtlTransactionManager* pTM);
  CStdioFile(FILE* pOpenStream);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parametry

*pOpenStream*<br/>
Określa wskaźnik pliku zwrócone przez wywołanie funkcji wykonawczej C [fopen —](../../c-runtime-library/reference/fopen-wfopen.md).

*lpszFileName*<br/>
Określa ciąg, który jest ścieżką do pliku. Ścieżka może być względna lub bezwzględna.

*nOpenFlags*<br/>
Określa opcje tworzenia plików, udostępnianie plików i tryby dostępu do pliku. Można określić wiele opcji za pomocą bitowej OR ( **|** ) — operator.

Jedną opcję Tryb dostępu do pliku jest wymagana. inne tryby są opcjonalne. Zobacz [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) Aby uzyskać listę opcji Tryb i inne flagi. W MFC w wersji 3.0 i nowszych udziału flagi są dozwolone.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor nie dołączyć plik do `CStdioFile` obiektu. Podczas używania tego konstruktora, należy użyć `CStdioFile::Open` metodę, aby otworzyć plik i dołączyć go do `CStdioFile` obiektu.

Konstruktor pojedynczego parametru dołącza strumień Otwórz plik `CStdioFile` obiektu. Dozwolone wartości wskaźnika obejmują wskaźniki wstępnie zdefiniowanych we/wy pliku *stdin*, *stdout*, lub *stderr*.

Tworzy konstruktora parametru dwóch `CStdioFile` obiektu i otwiera odpowiadający mu plik z określoną ścieżką.

W przypadku przekazania wartości NULL dla dowolnego *pOpenStream* lub *lpszFileName*, Konstruktor wyrzuca `CInvalidArgException*`.

Jeśli plik nie może otworzyć lub utworzyć, Konstruktor wyrzuca `CFileException*`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

##  <a name="m_pstream"></a>  CStdioFile::m_pStream

`m_pStream` Element członkowski danych jest wskaźnik do otwartego pliku, ponieważ zwrócona przez funkcję środowiska wykonawczego języka C `fopen`.

```
FILE* m_pStream;
```

### <a name="remarks"></a>Uwagi

Ma wartość NULL, jeśli plik nigdy nie otwierano lub został zamknięty.

##  <a name="open"></a>  CStdioFile::Open

Przeciążone. Otwórz jest przeznaczony do użytku przy użyciu domyślnego `CStdioFile` konstruktora.

```
virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Ciąg, który jest ścieżka do żądanego pliku. Ścieżka może być względna lub bezwzględna.

*nOpenFlags*<br/>
Tryb udostępnianiem i dostępem. Określa akcję wykonywaną podczas otwierania pliku. Opcje można połączyć za pomocą bitowej OR (&#124;) — operator. Uprawnienie dostępu jednego i jeden udział opcji są wymagane; tryby modeCreate i modeNoInherit są opcjonalne.

*pError*<br/>
Wskaźnik do istniejącego obiektu wyjątku plików, który zostanie wyświetlony stan operacji zakończonej niepowodzeniem.

*pTM*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli to się powiedzie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="readstring"></a>  CStdioFile::ReadString

Odczytuje dane tekstowe do buforu, w granicach *nmaks*-1 znaków, z pliku skojarzone z `CStdioFile` obiektu.

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Określa wskaźnik do buforu dostarczone przez użytkownika, który będzie otrzymywał ciąg tekstowy zakończony znakiem null.

*nmaks.*<br/>
Określa maksymalną liczbę znaków do odczytania, nie licząc zamykającego kończącego znaku null.

*rString*<br/>
Odwołanie do `CString` obiektu, który będzie zawierać ciąg, gdy funkcja zwraca.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do buforu zawierającą dane tekstowe. Wartość NULL, jeśli osiągnięto koniec pliku przed odczytaniem żadnych danych; czy osiągnięto wartość logiczna, wartość FALSE, jeśli koniec pliku przed odczytaniem danych.

### <a name="remarks"></a>Uwagi

Odczytywanie została zatrzymana przez pierwszy znak nowego wiersza. Jeśli w takim przypadku mniej niż *nmaks*odczytano znaków-1, znak nowego wiersza znajduje się w buforze. Znak null ('\0') jest dołączany w obu przypadkach.

[CFile::Read](../../mfc/reference/cfile-class.md#read) jest również dostępna dla danych wejściowych w trybie tekstowym, ale nie kończy w parę wysuwu wiersza powrotu karetki.

> [!NOTE]
>  `CString` Wersja tej funkcji spowoduje usunięcie `'\n'` Jeśli jest obecny; nie obsługuje wersji LPTSTR.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

##  <a name="seek"></a>  CStdioFile::Seek

Powoduje przeniesienie wskaźnika w wcześniej otwarty plik.

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lOff*<br/>
Liczba bajtów do przesuwania wskaźnika.

*nZe*<br/>
Tryb przenoszenia wskaźnika. Musi być jedną z następujących wartości:

- `CFile::begin`: Przesuń wskaźnik pliku *lOff* bajtów w przód od początku pliku.

- `CFile::current`: Przesuń wskaźnik pliku *lOff* bajtów z bieżącego położenia w pliku.

- `CFile::end`: Przesuń wskaźnik pliku *lOff* bajty od końca pliku. Należy pamiętać, że *lOff* musi być ujemna do wyszukania w istniejących plików; dodatnie wartości spowoduje przejście poza końcem pliku.

### <a name="return-value"></a>Wartość zwracana

Jeśli żądana pozycja jest legalny, `Seek` zwraca nowy przesunięcie w bajtach od początku pliku. W przeciwnym razie wartość zwracana jest niezdefiniowane i `CFileException` obiekt jest generowany.

### <a name="remarks"></a>Uwagi

`Seek` Funkcji zezwala na losowe dostęp do zawartości pliku, przenosząc kursor określony czas, absolutnie lub stosunkowo. Nie są faktycznie odczytywane dane podczas wyszukiwania. Jeśli żądana pozycja jest większy niż rozmiar pliku, długość pliku będzie obowiązywała do tej pozycji, a nie pojawi się wyjątek.

Po otwarciu pliku wskaźnika pliku jest umieszczony w przesunięciu 0, na początku pliku.

Ta implementacja `Seek` opiera się na funkcji biblioteki wykonawczej (CRT) `fseek`. Istnieje kilka ograniczeń dotyczących użycia `Seek` strumieni otwarty w trybie tekstowym. Aby uzyskać więcej informacji, zobacz [fseek, _fseeki64 —](../../c-runtime-library/reference/fseek-fseeki64.md).

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `Seek` umieszczenie wskaźnika myszy na 1000 bajtów od początku `cfile` pliku. Należy pamiętać, że `Seek` nie odczytuje danych, dzięki czemu później należy wywołać [CStdioFile::ReadString](#readstring) można odczytać danych.

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

##  <a name="writestring"></a>  CStdioFile::WriteString

Zapisuje dane z buforu do pliku związanego z `CStdioFile` obiektu.

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Określa wskaźnik do buforu, który zawiera ciąg zakończony znakiem null.

### <a name="remarks"></a>Uwagi

Kończącego znaku null ( `\0`) nie są zapisywane do pliku. Ta metoda zapisuje znaki nowego wiersza w *lpsz* do pliku jako pary return/wysuw wiersza powrotu karetki.

Jeśli chcesz zapisać danych, który nie jest zakończony wartością null do pliku, użyj `CStdioFile::Write` lub [CFile::Write](../../mfc/reference/cfile-class.md#write).

Ta metoda wyrzuca `CInvalidArgException*` Jeśli określono wartość NULL w przypadku *lpsz* parametru.

Ta metoda wyrzuca `CFileException*` w odpowiedzi na błędy systemu plików.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)<br/>
[CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)<br/>
[CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[Klasa CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)
