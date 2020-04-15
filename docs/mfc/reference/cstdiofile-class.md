---
title: Klasa CStdioFile
ms.date: 08/29/2019
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
ms.openlocfilehash: 80ee65aa339a38b3d8434bc4c7cb977e263f037b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366013"
---
# <a name="cstdiofile-class"></a>Klasa CStdioFile

Reprezentuje plik strumienia w czasie wykonywania języka C, otwarty przez funkcję wykonywania [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

## <a name="syntax"></a>Składnia

```
class CStdioFile : public CFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|Konstruuje `CStdioFile` obiekt ze ścieżki lub wskaźnika pliku.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStdioFile::Otwórz](#open)|Przeciążone. Open jest przeznaczony do `CStdioFile` użytku z domyślnym konstruktorem (Overrides [CFile::Open](../../mfc/reference/cfile-class.md#open)).|
|[CStdioFile::Odczyt](#readstring)|Odczytuje pojedynczy wiersz tekstu.|
|[CStdioFile::Szukaj](#seek)|Umieszcza bieżący wskaźnik pliku.|
|[CStdioFile::WriteString](#writestring)|Zapisuje pojedynczy wiersz tekstu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|Zawiera wskaźnik do otwartego pliku.|

## <a name="remarks"></a>Uwagi

Pliki strumienia są buforowane i mogą być otwierane w trybie tekstowym (domyślnym) lub binarnym.

Tryb tekstowy zapewnia specjalne przetwarzanie par wiersza powrotu karetki. Podczas pisania znaku kanału informacyjnego (newline) (0x0A) `CStdioFile` do obiektu trybu tekstowego do pliku jest wysyłana para bajtów (0x0D, 0x0A). Podczas czytania para bajtów (0x0D, 0x0A) jest tłumaczona na pojedynczy bajt 0x0A.

Funkcje [CFile](../../mfc/reference/cfile-class.md) [Duplicate](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange)i [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) nie są obsługiwane dla `CStdioFile`.

Jeśli wywołasz te `CStdioFile`funkcje na , otrzymasz [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Aby uzyskać więcej `CStdioFile`informacji na temat używania , zobacz artykuły [Pliki w MFC](../../mfc/files-in-mfc.md) i [Obsługa plików](../../c-runtime-library/file-handling.md) w *odwołaniu do biblioteki w czasie wykonywania*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cfile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="cstdiofilecstdiofile"></a><a name="cstdiofile"></a>CStdioFile::CStdioFile

Konstruuje i inicjuje `CStdioFile` obiekt.

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
Określa wskaźnik pliku zwrócony przez wywołanie funkcji wykonywania C [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

*lpszFileName*<br/>
Określa ciąg, który jest ścieżką do żądanego pliku. Ścieżka może być względna lub bezwzględna.

*nOpenLags*<br/>
Określa opcje tworzenia plików, udostępniania plików i trybów dostępu do plików. Można określić wiele opcji za pomocą **|** operatora bitowego OR ( ).

Wymagana jest opcja trybu dostępu do pliku; inne tryby są opcjonalne. Zobacz [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) listę opcji trybu i innych flag. W wersji MFC 3.0 i nowszych flagi udziału są dozwolone.

*Ptm*<br/>
Wskaźnik do obiektu CAtlTransactionManager.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor nie dołącza `CStdioFile` pliku do obiektu. Podczas korzystania z tego konstruktora, należy użyć `CStdioFile::Open` metody, `CStdioFile` aby otworzyć plik i dołączyć go do obiektu.

Konstruktor pojedynczego parametru dołącza otwarty `CStdioFile` strumień plików do obiektu. Dozwolone wartości wskaźnika obejmują wstępnie zdefiniowane wskaźniki pliku wejściowego/wyjściowego *stdin*, *stdout*lub *stderr*.

Konstruktor dwóch parametrów `CStdioFile` tworzy obiekt i otwiera odpowiedni plik z daną ścieżką.

Jeśli przekażesz NULL dla *pOpenStream* lub *lpszFileName*, `CInvalidArgException*`konstruktor zgłasza .

Jeśli nie można otworzyć lub utworzyć pliku, `CFileException*`konstruktor zgłasza plik .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

## <a name="cstdiofilem_pstream"></a><a name="m_pstream"></a>CStdioFile::m_pStream

Element `m_pStream` członkowski danych jest wskaźnikiem do otwartego pliku `fopen`zwróconego przez funkcję wykonywania C .

```
FILE* m_pStream;
```

### <a name="remarks"></a>Uwagi

Jest null, jeśli plik nigdy nie został otwarty lub został zamknięty.

## <a name="cstdiofileopen"></a><a name="open"></a>CStdioFile::Otwórz

Przeciążone. Open jest przeznaczony do `CStdioFile` użytku z konstruktorem domyślnym.

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
Ciąg, który jest ścieżką do żądanego pliku. Ścieżka może być względna lub bezwzględna.

*nOpenLags*<br/>
Tryb udostępniania i dostępu. Określa akcję, która należy podjąć podczas otwierania pliku. Opcje można łączyć za pomocą operatora bitowego OR (&#124;). Wymagane jest jedno uprawnienie dostępu i jedna opcja udziału; modeCreate i modeNoInherit tryby są opcjonalne.

*Perror*<br/>
Wskaźnik do istniejącego obiektu wyjątku pliku, który otrzyma stan operacji nie powiodło się.

*Ptm*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cstdiofilereadstring"></a><a name="readstring"></a>CStdioFile::Odczyt

Odczytuje dane tekstowe do buforu, do limitu znaków *nMax*-1, z pliku skojarzonego z obiektem. `CStdioFile`

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>Parametry

*lpsz (lpsz)*<br/>
Określa wskaźnik do buforu dostarczonego przez użytkownika, który otrzyma ciąg tekstowy zakończony z wartością null.

*Nmax*<br/>
Określa maksymalną liczbę znaków do odczytu, nie licząc kończącego się znaku null.

*rString*<br/>
Odwołanie do `CString` obiektu, który będzie zawierał ciąg, gdy funkcja zwraca.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do buforu zawierającego dane tekstowe. NULL, jeśli osiągnięto koniec pliku bez odczytu żadnych danych; lub jeśli wartość logiczna, FAŁSZ, jeśli osiągnięto koniec pliku bez odczytu żadnych danych.

### <a name="remarks"></a>Uwagi

Odczyt jest zatrzymywany przez pierwszy znak nowego tekstu. Jeśli w takim przypadku odczytano mniej niż *nMax*-1 znaków, znak nowego typu jest przechowywany w buforze. Znak zerowy ('\0') jest dołączany w obu przypadkach.

[CFile::Read](../../mfc/reference/cfile-class.md#read) jest również dostępny dla danych wejściowych w trybie tekstowym, ale nie kończy się na parze kanału informacyjnego wiersza powrotu karetki.

> [!NOTE]
> `CString` Wersja tej funkcji usuwa `'\n'` if present; wersja LPTSTR nie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

## <a name="cstdiofileseek"></a><a name="seek"></a>CStdioFile::Szukaj

Zmienia położenie wskaźnika w wcześniej otwartym pliku.

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lOff (wyjęcie*<br/>
Liczba bajtów, aby przesunąć wskaźnik.

*nZ*<br/>
Tryb ruchu wskaźnika. Musi mieć jedną z następujących wartości:

- `CFile::begin`: Od początku pliku przesuwanie wskaźnika pliku *lOff* bajtów do przodu.

- `CFile::current`: Przenieś wskaźnik pliku *lOff* bajtów z bieżącej pozycji w pliku.

- `CFile::end`: Przenieś wskaźnik pliku *lOff* bajtów od końca pliku. Należy zauważyć, że *lOff* musi być ujemny, aby szukać w istniejącym pliku; wartości dodatnie będą poszukiwać po zakończeniu pliku.

### <a name="return-value"></a>Wartość zwracana

Jeśli żądane stanowisko jest `Seek` legalne, zwraca nowe przesunięcie bajtu od początku pliku. W przeciwnym razie zwracana wartość jest `CFileException` niezdefiniowana i obiekt jest generowany.

### <a name="remarks"></a>Uwagi

Funkcja `Seek` umożliwia losowy dostęp do zawartości pliku, przesuwając wskaźnik określoną kwotę, absolutnie lub stosunkowo. Żadne dane nie są faktycznie odczytywane podczas poszukiwania. Jeśli żądana pozycja jest większa niż rozmiar pliku, długość pliku zostanie rozszerzona do tej pozycji i nie zostanie zgłoszony wyjątek.

Po otwarciu pliku wskaźnik pliku jest umieszczany na odsunięciu 0, czyli na początku pliku.

Ta implementacja `Seek` jest oparta na funkcji `fseek`biblioteki wykonawczej (CRT). Istnieje kilka ograniczeń dotyczących `Seek` korzystania z strumieni otwartych w trybie tekstowym. Aby uzyskać więcej informacji, zobacz [fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md).

### <a name="example"></a>Przykład

W poniższym przykładzie `Seek` pokazano, jak użyć do przenoszenia wskaźnika `cfile` 1000 bajtów od początku pliku. Należy `Seek` zauważyć, że nie odczytuje danych, więc należy następnie wywołać [CStdioFile::ReadString](#readstring) do odczytu danych.

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

## <a name="cstdiofilewritestring"></a><a name="writestring"></a>CStdioFile::WriteString

Zapisuje dane z bufora do pliku `CStdioFile` skojarzonego z obiektem.

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parametry

*lpsz (lpsz)*<br/>
Określa wskaźnik do buforu zawierającego ciąg zakończony zerem.

### <a name="remarks"></a>Uwagi

Kończący się znak `\0`null ( ) nie jest zapisywany w pliku. Ta metoda zapisuje znaki nowego wiersza w *lpsz* do pliku jako parą wiersza powrotu karetki.

Jeśli chcesz zapisać dane, które nie są zakończone z `CStdioFile::Write` wartością null do pliku, użyj lub [CFile::Write](../../mfc/reference/cfile-class.md#write).

Ta metoda `CInvalidArgException*` zgłasza, jeśli określisz NULL dla *lpsz* parametru.

Ta metoda zgłasza `CFileException*` w odpowiedzi na błędy systemu plików.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[CFile::Dzliklikalikacji](../../mfc/reference/cfile-class.md#duplicate)<br/>
[CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)<br/>
[Plik C::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[Klasa CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)
