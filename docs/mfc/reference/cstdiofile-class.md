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
ms.openlocfilehash: 068e59fdc19821487bc78141d10743363221518e
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375834"
---
# <a name="cstdiofile-class"></a>Klasa CStdioFile

Reprezentuje plik strumienia uruchomieniowego C, który został otwarty przez funkcję Run-Time [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

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
|[CStdioFile::Open](#open)|Przeciążone. Otwórz jest przeznaczony do użytku z konstruktorem `CStdioFile` domyślnym (Przesłania [CFile:: Open](../../mfc/reference/cfile-class.md#open)).|
|[CStdioFile::ReadString](#readstring)|Odczytuje pojedynczy wiersz tekstu.|
|[CStdioFile::Seek](#seek)|Określa położenie bieżącego wskaźnika pliku.|
|[CStdioFile::WriteString](#writestring)|Zapisuje pojedynczy wiersz tekstu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|Zawiera wskaźnik do otwartego pliku.|

## <a name="remarks"></a>Uwagi

Pliki strumieni są buforowane i mogą być otwierane w trybie tekstowym (ustawienie domyślne) lub w trybie binarnym.

Tryb tekstu zapewnia specjalne przetwarzanie par kanałów powrotu karetki. Po napisaniu znaku wysuwu wiersza (z wierszem) (0x0A) do obiektu trybu `CStdioFile` tekstowego para bajtów (0x0D, 0x0A) jest wysyłana do pliku. Podczas odczytywania para bajtów (0x0D, 0x0A) jest tłumaczona na jeden bajt.

[Duplikaty](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange)i [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) funkcji `CStdioFile` [CFile](../../mfc/reference/cfile-class.md) nie są obsługiwane w programie.

Jeśli wywołasz te funkcje w `CStdioFile`, uzyskasz [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Aby uzyskać więcej informacji na `CStdioFile`temat korzystania z programu, zapoznaj się z artykułami [pliki w bibliotece MFC](../../mfc/files-in-mfc.md) i [Obsługa plików](../../c-runtime-library/file-handling.md) w *dokumentacji dotyczącej biblioteki wykonawczej*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="cstdiofile"></a>CStdioFile::CStdioFile

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
Określa wskaźnik pliku zwracany przez wywołanie funkcji C Run-Time [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

*lpszFileName*<br/>
Określa ciąg, który jest ścieżką do żądanego pliku. Ścieżka może być względna lub bezwzględna.

*nOpenFlags*<br/>
Określa opcje tworzenia plików, udostępniania plików i tryb dostępu do plików. Można określić wiele opcji za pomocą operatora bitowego lub ( **|** ).

Wymagana jest tylko jedna opcja trybu dostępu do pliku; inne tryby są opcjonalne. Aby zapoznać się z listą opcji trybu i innych flag, zobacz [CFile:: CFile](../../mfc/reference/cfile-class.md#cfile) . W MFC w wersji 3,0 i nowszych flagi udostępniania są dozwolone.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager.

### <a name="remarks"></a>Uwagi

Konstruktor domyślny nie dołącza pliku do `CStdioFile` obiektu. W przypadku korzystania z tego konstruktora należy użyć `CStdioFile::Open` metody, aby otworzyć plik i dołączyć go `CStdioFile` do obiektu.

Konstruktor jednego parametru dołącza do `CStdioFile` obiektu strumień otwartych plików. Dozwolone wartości wskaźnika obejmują wstępnie zdefiniowane wskaźniki pliku wejściowego/wyjściowego *stdin*, *stdout*lub *stderr*.

Konstruktor dwuparametrowy tworzy `CStdioFile` obiekt i otwiera odpowiadający mu plik z daną ścieżką.

W przypadku przekazania wartości NULL dla *pOpenStream* lub *lpszFileName* `CInvalidArgException*`Konstruktor zgłosi.

Jeśli plik nie może zostać otwarty lub utworzony, Konstruktor zgłosi `CFileException*`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

##  <a name="m_pstream"></a>  CStdioFile::m_pStream

Element członkowski `fopen`danych jest wskaźnikiem do otwartego pliku, który został zwrócony przez funkcję C Run-Time. `m_pStream`

```
FILE* m_pStream;
```

### <a name="remarks"></a>Uwagi

Jeśli plik nigdy nie został otwarty lub został zamknięty, ma wartość NULL.

##  <a name="open"></a>CStdioFile:: Open

Przeciążone. Otwórz jest przeznaczony do użytku z konstruktorem `CStdioFile` domyślnym.

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

*nOpenFlags*<br/>
Tryb udostępniania i dostępu. Określa akcję, która ma zostać podjęta podczas otwierania pliku. Opcje można łączyć za pomocą operatora bitowego lub (&#124;). Wymagane są jedno uprawnienie dostępu i jedna opcja udostępniania; tryby modeCreate i modeNoInherit są opcjonalne.

*pError*<br/>
Wskaźnik do istniejącego obiektu wyjątku pliku, który otrzyma stan operacji zakończonej niepowodzeniem.

*pTM*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="readstring"></a>CStdioFile::ReadString

Odczytuje dane tekstowe do buforu, do limitu *nmaks.* -1 znaków, z pliku skojarzonego z `CStdioFile` obiektem.

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Określa wskaźnik do buforu dostarczonego przez użytkownika, który będzie otrzymywał ciąg tekstowy zakończony wartością null.

*Nmaks.*<br/>
Określa maksymalną liczbę znaków do odczytania, która nie zlicza kończącego znaku null.

*rString*<br/>
Odwołanie do `CString` obiektu, który będzie zawierać ciąg, gdy funkcja zwraca wartość.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do buforu zawierającego dane tekstowe. Wartość NULL, jeśli koniec pliku został osiągnięty bez odczytywania danych; lub jeśli wartość logiczna jest RÓWNa FALSE, jeśli koniec pliku został osiągnięty bez odczytywania danych.

### <a name="remarks"></a>Uwagi

Odczyt jest zatrzymywany przez pierwszy znak nowego wiersza. Jeśli w tym przypadku nie przeczytano więcej niż *nmaks.* znaków, znak nowego wiersza jest przechowywany w buforze. W obu przypadkach dołączany jest znak null (' \ 0 ').

[CFile:: Read](../../mfc/reference/cfile-class.md#read) jest również dostępna dla danych wejściowych w trybie tekstowym, ale nie kończy się na parze wysuwu wiersza powrotu karetki.

> [!NOTE]
>  Wersja tej funkcji `'\n'` usuwa jeśli obecny; wersja LPTStr nie. `CString`

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

##  <a name="seek"></a>CStdioFile:: Seek

Zmienia położenie wskaźnika w wcześniej otwartym pliku.

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lOff*<br/>
Liczba bajtów do przeniesienia wskaźnika.

*nFrom*<br/>
Tryb przenoszenia wskaźnika. Musi mieć jedną z następujących wartości:

- `CFile::begin`: Przenieś wskaźnik pliku *lOff* bajty do przodu od początku pliku.

- `CFile::current`: Przenieś wskaźnik pliku *lOff* bajty z bieżącej pozycji w pliku.

- `CFile::end`: Przenieś wskaźnik pliku *lOff* bajty z końca pliku. Należy pamiętać, że *lOff* musi być ujemna, aby przeszukiwać istniejący plik; wartości dodatnie będą przebiegać poza końcem pliku.

### <a name="return-value"></a>Wartość zwracana

Jeśli żądana pozycja jest legalna, `Seek` zwraca nowe przesunięcie bajtu od początku pliku. W przeciwnym razie wartość zwracana jest niezdefiniowana i `CFileException` zwracany jest obiekt.

### <a name="remarks"></a>Uwagi

`Seek` Funkcja zezwala na losowy dostęp do zawartości pliku przez przeniesienie wskaźnika o określoną ilość, absolutną lub względną. Podczas wyszukiwania nie są faktycznie odczytywane żadne dane. Jeśli żądana pozycja jest większa niż rozmiar pliku, długość pliku zostanie rozszerzona do tej pozycji i żaden wyjątek nie zostanie wygenerowany.

Gdy plik zostanie otwarty, wskaźnik pliku jest ustawiany przy przesunięciu 0, początku pliku.

Ta implementacja programu `Seek` jest oparta na funkcji `fseek`biblioteki wykonawczej (CRT). Istnieje kilka ograniczeń dotyczących użycia `Seek` strumieni otwartych w trybie tekstowym. Aby uzyskać więcej informacji, zobacz [fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md).

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak użyć `Seek` , aby przenieść wskaźnik 1000 bajtów od początku `cfile` pliku. Należy pamiętać `Seek` , że dane nie są odczytywane, dlatego należy wywołać [CStdioFile:: ReadString](#readstring) w celu odczytania danych.

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

##  <a name="writestring"></a>CStdioFile::WriteString

Zapisuje dane z buforu do pliku skojarzonego z `CStdioFile` obiektem.

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Określa wskaźnik do buforu, który zawiera ciąg zakończony znakiem null.

### <a name="remarks"></a>Uwagi

Kończący znak null ( `\0`) nie jest zapisywana w pliku. Ta metoda zapisuje znaki nowego wiersza w *lpsz* do pliku jako parę wysuw kanału powrotu karetki.

Jeśli chcesz zapisać dane, które nie są zakończone znakiem null do pliku, użyj `CStdioFile::Write` lub [CFile:: Write](../../mfc/reference/cfile-class.md#write).

Ta metoda zgłasza `CInvalidArgException*` wartość null dla parametru *lpsz* .

Ta metoda zgłasza `CFileException*` w odpowiedzi na błędy systemu plików.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>Zobacz także

[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)<br/>
[CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)<br/>
[CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[Klasa CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)
