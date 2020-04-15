---
title: Klasa CFile
ms.date: 06/12/2018
f1_keywords:
- CFile
- AFX/CFile
- AFX/CFile::CFile
- AFX/CFile::Abort
- AFX/CFile::Close
- AFX/CFile::Duplicate
- AFX/CFile::Flush
- AFX/CFile::GetFileName
- AFX/CFile::GetFilePath
- AFX/CFile::GetFileTitle
- AFX/CFile::GetLength
- AFX/CFile::GetPosition
- AFX/CFile::GetStatus
- AFX/CFile::LockRange
- AFX/CFile::Open
- AFX/CFile::Read
- AFX/CFile::Remove
- AFX/CFile::Rename
- AFX/CFile::Seek
- AFX/CFile::SeekToBegin
- AFX/CFile::SeekToEnd
- AFX/CFile::SetFilePath
- AFX/CFile::SetLength
- AFX/CFile::SetStatus
- AFX/CFile::UnlockRange
- AFX/CFile::Write
- AFX/CFile::hFileNull
- AFX/CFile::m_hFile
- AFX/CFile::m_pTM
helpviewer_keywords:
- CFile [MFC], CFile
- CFile [MFC], Abort
- CFile [MFC], Close
- CFile [MFC], Duplicate
- CFile [MFC], Flush
- CFile [MFC], GetFileName
- CFile [MFC], GetFilePath
- CFile [MFC], GetFileTitle
- CFile [MFC], GetLength
- CFile [MFC], GetPosition
- CFile [MFC], GetStatus
- CFile [MFC], LockRange
- CFile [MFC], Open
- CFile [MFC], Read
- CFile [MFC], Remove
- CFile [MFC], Rename
- CFile [MFC], Seek
- CFile [MFC], SeekToBegin
- CFile [MFC], SeekToEnd
- CFile [MFC], SetFilePath
- CFile [MFC], SetLength
- CFile [MFC], SetStatus
- CFile [MFC], UnlockRange
- CFile [MFC], Write
- CFile [MFC], hFileNull
- CFile [MFC], m_hFile
- CFile [MFC], m_pTM
ms.assetid: b2eb5757-d499-4e67-b044-dd7d1abaa0f8
ms.openlocfilehash: 4ba37d481db73fb0556659ede267b3474c3f32f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373922"
---
# <a name="cfile-class"></a>Klasa CFile

Klasa podstawowa dla klas plików klasy Programu Microsoft Foundation.

## <a name="syntax"></a>Składnia

```
class CFile : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Plik C::CFile](#cfile)|Konstruuje `CFile` obiekt ze ścieżki lub dojścia do pliku.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFile::Przerwanie](#abort)|Zamyka plik ignorując wszystkie ostrzeżenia i błędy.|
|[CFile::Zamknij](#close)|Zamyka plik i usuwa obiekt.|
|[CFile::Dzliklikalikacji](#duplicate)|Tworzy zduplikowany obiekt na podstawie tego pliku.|
|[CFile::Opróżnianie](#flush)|Opróżnia wszystkie dane, które mają zostać zapisane.|
|[Plik C::GetFileName](#getfilename)|Pobiera nazwę pliku wybranego pliku.|
|[CFile::GetFilePath](#getfilepath)|Pobiera pełną ścieżkę pliku wybranego pliku.|
|[Plik C::GetFileTitle](#getfiletitle)|Pobiera tytuł wybranego pliku.|
|[Plik C::GetLength](#getlength)|Pobiera długość pliku.|
|[Plik C::GetPosition](#getposition)|Pobiera bieżący wskaźnik pliku.|
|[Plik C::GetStatus](#getstatus)|Pobiera stan otwartego pliku lub w wersji statycznej, pobiera stan określonego pliku (funkcja statyczna, wirtualna).|
|[CFile::LockRange](#lockrange)|Blokuje zakres bajtów w pliku.|
|[Plik C::Otwórz](#open)|Bezpiecznie otwiera plik z opcją testowania błędów.|
|[Plik C::Odczyt](#read)|Odczytuje (niebuforowane) dane z pliku w bieżącym położeniu pliku.|
|[CFile::Usuń](#remove)|Usuwa określony plik (funkcja statyczna).|
|[CFile::Zmień nazwę](#rename)|Zmienia nazwę określonego pliku (funkcja statyczna).|
|[Plik C::Szukaj](#seek)|Umieszcza bieżący wskaźnik pliku.|
|[CFile::SeekToBegin](#seektobegin)|Umieszcza bieżący wskaźnik pliku na początku pliku.|
|[Plik C::SeekToEnd](#seektoend)|Umieszcza bieżący wskaźnik pliku na końcu pliku.|
|[CFile::SetFilePath](#setfilepath)|Ustawia pełną ścieżkę pliku wybranego pliku.|
|[Plik C::SetLength](#setlength)|Zmienia długość pliku.|
|[CFile::SetStatus](#setstatus)|Ustawia stan określonego pliku (funkcja statyczna, wirtualna).|
|[Plik C::UnlockRange](#unlockrange)|Odblokowuje zakres bajtów w pliku.|
|[CFile::Zapis](#write)|Zapisuje (niebuforowane) dane w pliku do bieżącej pozycji pliku.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFile::uchwyt operatora](#operator_handle)|Dojście `CFile` do obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[Plik C::hFileNull](#hfilenull)|Określa, `CFile` czy obiekt ma prawidłowy dojście.|
|[CFile::m_hFile](#m_hfile)|Zwykle zawiera dojście do pliku systemu operacyjnego.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CFile::m_pTM](#m_ptm)|Wskaźnik `CAtlTransactionManager` do obiektu.|

## <a name="remarks"></a>Uwagi

Bezpośrednio zapewnia niebuforowane, binarne usługi wejściowe/wyjściowe dysku i pośrednio obsługuje pliki tekstowe i pliki pamięci za pośrednictwem klas pochodnych. `CFile`działa w połączeniu `CArchive` z klasą do obsługi serializacji obiektów Microsoft Foundation Class.

Hierarchiczna relacja między tą klasą a jej klasami pochodnymi umożliwia programowi działanie `CFile` na wszystkich obiektach plików za pośrednictwem interfejsu polimorficznego. Plik pamięci, na przykład, zachowuje się jak plik dysku.

Użyj `CFile` i jego klas pochodnych dla ogólnego przeznaczenia we/wy dysku. Użyj `ofstream` lub `iostream` innych klas firmy Microsoft dla sformatowanego tekstu wysyłanego do pliku dysku.

Zwykle plik dysku jest otwierany `CFile` automatycznie na budowie i zamykany po zniszczeniu. Statyczne funkcje członkowskie umożliwiają przesłuchiwanie stanu pliku bez otwierania pliku.

Aby uzyskać więcej `CFile`informacji na temat używania , zobacz artykuły [Pliki w MFC](../../mfc/files-in-mfc.md) i [Obsługa plików](../../c-runtime-library/file-handling.md) w *odwołaniu do biblioteki w czasie wykonywania*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="cfileabort"></a><a name="abort"></a>CFile::Przerwanie

Zamyka plik skojarzony z tym obiektem i sprawia, że plik jest niedostępny do odczytu lub zapisu.

```
virtual void Abort();
```

### <a name="remarks"></a>Uwagi

Jeśli plik nie został zamknięty przed zniszczeniem obiektu, destruktor zamknie go za Ciebie.

Podczas obsługi wyjątków, `CFile::Abort` `CFile::Close` różni się od dwóch ważnych sposobów. Po pierwsze `Abort` funkcja nie zgłasza wyjątek na błędy, ponieważ błędy `Abort`są ignorowane przez . Po `Abort` drugie nie będzie **assert,** jeśli plik nie został otwarty lub został zamknięty wcześniej.

Jeśli użyto **nowego** `CFile` do przydzielenia obiektu na stosie, należy go usunąć po zamknięciu pliku. `Abort`ustawia `m_hFile` `CFile::hFileNull`się na .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

## <a name="cfilecfile"></a><a name="cfile"></a>Plik C::CFile

Konstruuje i inicjuje `CFile` obiekt.

```
CFile();
CFile(CAtlTransactionManager* pTM);
CFile(HANDLE hFile);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags,
CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parametry

*hFile (plik)*<br/>
Dojście pliku do `CFile` dołączenia do obiektu.

*lpszFileName*<br/>
Względna lub pełna ścieżka pliku `CFile` do dołączenia do obiektu.

*nOpenLags*<br/>
Kombinacja bitowa (OR) opcji dostępu do plików dla określonego pliku. Zobacz uwagi sekcji możliwych opcji.

*Ptm*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

W poniższych pięciu tabelach przedstawiono możliwe opcje parametru *nOpenFlags.*

Wybierz tylko jedną z następujących opcji trybu dostępu do plików. Domyślnym trybem `CFile::modeRead`dostępu do plików jest tryb tylko do odczytu.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::modeRead`|Żąda tylko dostępu do odczytu.|
|`CFile::modeWrite`|Żąda tylko dostępu do zapisu.|
|`CFile::modeReadWrite`|Żąda dostępu do odczytu i zapisu.|

Wybierz jedną z następujących opcji trybu znakowego.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::typeBinary`|Ustawia tryb binarny (używany tylko w klasach pochodnych).|
|`CFile::typeText`|Ustawia tryb tekstu ze specjalnym przetwarzaniem dla par podajników linii powrotu karetki (używany tylko w klasach pochodnych).|
|`CFile::typeUnicode`|Ustawia tryb Unicode (używany tylko w klasach pochodnych). Tekst jest zapisywany do pliku w formacie Unicode, gdy aplikacja jest wbudowana w konfiguracji Unicode. W pliku nie jest zapisywany żaden BOM.|

Wybierz tylko jedną z następujących opcji trybu udostępniania plików. Domyślnym trybem `CFile::shareExclusive`udostępniania plików jest , który jest wyłączny.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::shareDenyNone`|Brak ograniczeń udostępniania.|
|`CFile::shareDenyRead`|Odmawia dostępu do odczytu do wszystkich innych.|
|`CFile::shareDenyWrite`|Odmawia dostępu do zapisu do wszystkich innych.|
|`CFile::shareExclusive`|Odmawia dostępu do odczytu i zapisu do wszystkich innych.|

Wybierz pierwszą lub obie opcje następującego trybu tworzenia plików. Domyślnym trybem `CFile::modeNoTruncate`tworzenia jest , który jest otwarty istniejący.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::modeCreate`|Tworzy nowy plik, jeśli nie istnieje żaden plik. Jeśli plik już istnieje, jest zastępowany i początkowo ustawiony na zerową długość.|
|`CFile::modeNoTruncate`|Tworzy nowy plik, jeśli nie istnieje żaden plik; w przeciwnym razie, jeśli plik już istnieje, `CFile` jest dołączony do obiektu.|

Wybierz następujące opcje buforowania plików zgodnie z opisem. Domyślnie system używa ogólnego zastosowania schematu buforowania, który nie jest dostępny jako opcja.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::osNoBuffer`|System nie używa pośredniej pamięci podręcznej dla pliku. Ta opcja powoduje anulowanie następujących 2 opcji.|
|`CFile::osRandomAccess`|Pamięć podręczna plików jest zoptymalizowana pod kątem dostępu losowego. Nie używaj zarówno tej opcji, jak i opcji skanowania sekwencyjnego.|
|`CFile::osSequentialScan`|Pamięć podręczna plików jest zoptymalizowana pod kątem dostępu sekwencyjnego. Nie używaj zarówno tej opcji, jak i opcji dostępu losowego.|
|`CFile::osWriteThrough`|Operacje zapisu są wykonywane bez opóźnień.|

Wybierz następującą opcję zabezpieczeń, aby zapobiec dziedziczeniu dojścia pliku. Domyślnie wszystkie nowe procesy podrzędne mogą używać dojścia do pliku.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::modeNoInherit`|Zapobiega procesom podrzędnym korzystania z uchwytu pliku.|

Domyślny konstruktor inicjuje elementy członkowskie, `CFile` ale nie dołącza pliku do obiektu. Po użyciu tego konstruktora użyj [CFile::Open](#open) metody, aby `CFile` otworzyć plik i dołączyć go do obiektu.

Konstruktor z jednym parametrem inicjuje elementy `CFile` członkowskie i dołącza istniejący plik do obiektu.

Konstruktor z dwoma parametrami inicjuje elementy członkowskie i próbuje otworzyć określony plik. Jeśli ten konstruktor pomyślnie otworzy określony plik, `CFile` plik zostanie dołączony do obiektu; w przeciwnym razie ten konstruktor `CInvalidArgException` rzuca wskaźnik do obiektu. Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [Wyjątki](../../mfc/exception-handling-in-mfc.md).

Jeśli `CFile` obiekt pomyślnie otworzy określony plik, zostanie on automatycznie `CFile` zamknięty po zniszczeniu obiektu; w przeciwnym razie należy jawnie zamknąć plik po jego `CFile` nie jest już dołączony do obiektu.

### <a name="example"></a>Przykład

Poniższy kod pokazuje, `CFile`jak używać pliku .

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

## <a name="cfileclose"></a><a name="close"></a>CFile::Zamknij

Zamyka plik skojarzony z tym obiektem i sprawia, że plik jest niedostępny do odczytu lub zapisu.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Jeśli plik nie został zamknięty przed zniszczeniem obiektu, destruktor zamknie go za Ciebie.

Jeśli użyto **nowego** `CFile` do przydzielenia obiektu na stosie, należy go usunąć po zamknięciu pliku. `Close`ustawia `m_hFile` `CFile::hFileNull`się na .

### <a name="example"></a>Przykład

Zobacz przykład [CFile::CFile](#cfile).

## <a name="cfileduplicate"></a><a name="duplicate"></a>CFile::Dzliklikalikacji

Tworzy zduplikowany `CFile` obiekt dla danego pliku.

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do zduplikowanego `CFile` obiektu.

### <a name="remarks"></a>Uwagi

Ta funkcja jest równoważna funkcji `_dup`czasu wykonywania języka C .

## <a name="cfileflush"></a><a name="flush"></a>CFile::Opróżnianie

Wymusza zapisanie wszystkich danych pozostających w buforze plików w pliku.

```
virtual void Flush();
```

### <a name="remarks"></a>Uwagi

Użycie `Flush` nie gwarantuje opróżniania buforów. `CArchive` Jeśli używasz archiwum, zadzwoń [CArchive::Flush](../../mfc/reference/carchive-class.md#flush) pierwszy.

### <a name="example"></a>Przykład

Zobacz przykład [CFile::SetFilePath](#setfilepath).

## <a name="cfilegetfilename"></a><a name="getfilename"></a>Plik C::GetFileName

Wywołanie tej funkcji elementu członkowskiego, aby pobrać nazwę określonego pliku.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa pliku.

### <a name="remarks"></a>Uwagi

Na przykład podczas `GetFileName` wywoływania, aby wygenerować `c:\windows\write\myfile.wri`wiadomość do użytkownika `myfile.wri`o pliku , nazwa pliku, jest zwracany.

Aby zwrócić całą ścieżkę pliku, w tym nazwę, zadzwoń do [getfilepath](#getfilepath). Aby zwrócić tytuł pliku `myfile`( ), zadzwoń [do GetFileTitle](#getfiletitle).

### <a name="example"></a>Przykład

Ten fragment kodu otwiera system. w katalogu WINDOWS. Jeśli zostanie znaleziony, w przykładzie zostanie wydrukowana nazwa i ścieżka oraz tytuł, jak pokazano w obszarze Dane wyjściowe:

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

## <a name="cfilegetfilepath"></a><a name="getfilepath"></a>CFile::GetFilePath

Wywołanie tej funkcji elementu członkowskiego, aby pobrać pełną ścieżkę określonego pliku.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Wartość zwracana

Pełna ścieżka określonego pliku.

### <a name="remarks"></a>Uwagi

Na przykład podczas `GetFilePath` wywoływania, aby wygenerować `c:\windows\write\myfile.wri`wiadomość do `c:\windows\write\myfile.wri`użytkownika o pliku , ścieżka pliku, jest zwracany.

Aby zwrócić tylko nazwę pliku`myfile.wri`( ), wywołaj [getfilename](#getfilename). Aby zwrócić tytuł pliku`myfile`( ), zadzwoń [do GetFileTitle](#getfiletitle).

### <a name="example"></a>Przykład

Zobacz przykład [GetFileName](#getfilename).

## <a name="cfilegetfiletitle"></a><a name="getfiletitle"></a>Plik C::GetFileTitle

Wywołanie tej funkcji elementu członkowskiego, aby pobrać tytuł pliku (nazwę wyświetlaną) dla pliku.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Wartość zwracana

Tytuł pliku źródłowego.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [GetFileTitle,](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) aby pobrać tytuł pliku. Jeśli to się powiedzie, metoda zwraca ciąg, który system będzie używany do wyświetlania nazwy pliku do użytkownika. W przeciwnym razie metoda wywołuje [PathFindFileName,](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) aby pobrać nazwę pliku (w tym rozszerzenie pliku) pliku źródłowego. Oznacza to, że rozszerzenie pliku nie zawsze jest zawarte w ciągu tytuł zwracany plik. Aby uzyskać więcej informacji, zobacz [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) i [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) w usłudze Windows SDK.

Aby zwrócić całą ścieżkę pliku, w tym nazwę, zadzwoń do [getfilepath](#getfilepath). Aby zwrócić tylko nazwę pliku, zadzwoń [do GetFileName](#getfilename).

### <a name="example"></a>Przykład

Zobacz przykład [GetFileName](#getfilename).

## <a name="cfilegetlength"></a><a name="getlength"></a>Plik C::GetLength

Uzyskuje bieżącą długość logiczną pliku w bajtach.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

## <a name="cfilegetposition"></a><a name="getposition"></a>Plik C::GetPosition

Uzyskuje bieżącą wartość wskaźnika pliku, który może być `Seek`używany w późniejszych wywołaniach do .

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

## <a name="cfilegetstatus"></a><a name="getstatus"></a>Plik C::GetStatus

Ta metoda pobiera informacje o `CFile` stanie związane z danym wystąpieniem obiektu lub daną ścieżką pliku.

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*rStatus*<br/>
Odwołanie do struktury dostarczonej przez `CFileStatus` użytkownika, która otrzyma informacje o stanie. Struktura `CFileStatus` ma następujące pola:

- `CTime m_ctime`Data i godzina utworzenia pliku.

- `CTime m_mtime`Data i godzina ostatniej modyfikacji pliku.

- `CTime m_atime`Data i godzina ostatniego dostępu do pliku do odczytu.

- `ULONGLONG m_size`Logiczny rozmiar pliku w bajtach, zgodnie z poleceniem DIR.

- `BYTE m_attribute`Bajt atrybutu pliku.

- `char m_szFullName[_MAX_PATH]`Bezwzględna nazwa pliku w zestawie znaków systemu Windows.

*lpszFileName*<br/>
Ciąg w zestawie znaków systemu Windows, który jest ścieżką do żądanego pliku. Ścieżka może być względna lub bezwzględna lub może zawierać nazwę ścieżki sieciowej.

*Ptm*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli informacje o stanie określonego pliku zostały pomyślnie uzyskane; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Niestatyczna wersja `GetStatus` pobiera informacje o stanie otwartego pliku `CFile` skojarzonego z danym obiektem.  Statyczna wersja `GetStatus` uzyskuje stan pliku z danej ścieżki pliku bez faktycznego otwierania pliku. Ta wersja jest przydatna do testowania istnienia i praw dostępu do pliku.

Element `m_attribute` członkowski `CFileStatus` struktury odwołuje się do zestawu atrybutów pliku. Klasa `CFile` udostępnia typ wyliczenia **atrybutów,** dzięki czemu atrybuty plików mogą być określone symbolicznie:

```
enum Attribute {
    normal =    0x00,
    readOnly =  0x01,
    hidden =    0x02,
    system =    0x04,
    volume =    0x08,
    directory = 0x10,
    archive =   0x20
    };
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#10](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_6.cpp)]

## <a name="cfilehfilenull"></a><a name="hfilenull"></a>Plik C::hFileNull

Określa obecność prawidłowego dojścia `CFile` do pliku dla obiektu.

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>Uwagi

Ta stała jest używana `CFile` do określenia, czy obiekt ma prawidłowy uchwyt pliku.

Poniższy przykład pokazuje tę operację:

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

## <a name="cfilelockrange"></a><a name="lockrange"></a>CFile::LockRange

Blokuje zakres bajtów w otwartym pliku, zgłaszając wyjątek, jeśli plik jest już zablokowany.

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parametry

*dwPos (właśc.*<br/>
Przesunięcie bajtów początkowego zakresu bajtów do zablokowania.

*dwCount (licz)*<br/>
Liczba bajtów w zakresie do zablokowania.

### <a name="remarks"></a>Uwagi

Blokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Można zablokować więcej niż jeden region pliku, ale nie nakładające się regiony są dozwolone.

Po odblokowaniu regionu `UnlockRange` przy użyciu funkcji elementu członkowskiego zakres bajtów musi odpowiadać dokładnie regionowi, który został wcześniej zablokowany. Funkcja `LockRange` nie scala sąsiednich regionów. Jeśli sąsiadują dwa zablokowane regiony, należy odblokować każdy region oddzielnie.

> [!NOTE]
> Ta funkcja nie jest `CMemFile`dostępna dla klasy pochodnej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilem_hfile"></a><a name="m_hfile"></a>CFile::m_hFile

Zawiera dojście do pliku systemu operacyjnego dla otwartego pliku.

```
HANDLE m_hFile;
```

### <a name="remarks"></a>Uwagi

`m_hFile`jest zmienną publiczną typu UINT. Zawiera `CFile::hFileNull`on akces do pustego pliku niezależny od systemu operacyjnego, jeśli uchwyt nie został przypisany.

Użycie `m_hFile` nie jest zalecane, ponieważ znaczenie elementu członkowskiego zależy od klasy pochodnej. `m_hFile`jest członkiem publicznym dla wygody we wspieraniu niepolimorficznego korzystania z klasy.

## <a name="cfilem_ptm"></a><a name="m_ptm"></a>CFile::m_pTM

Wskaźnik do `CAtlTransactionManager` obiektu.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Uwagi

## <a name="cfileopen"></a><a name="open"></a>Plik C::Otwórz

Przeciążone. `Open`jest przeznaczony do użytku `CFile` z konstruktorem domyślnym.

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
Ciąg zawierający ścieżkę do żądanego pliku. Ścieżka może być względna, bezwzględna lub nazwa sieciowa (UNC).

*nOpenLags*<br/>
UINT, który definiuje tryb udostępniania i dostępu pliku. Określa akcję, która należy podjąć podczas otwierania pliku. Opcje można łączyć za pomocą operatora bitowego OR **(&#124;).** Wymagane jest jedno uprawnienie dostępu i jedna opcja udziału; `modeCreate` tryby `modeNoInherit` są opcjonalne. Zobacz konstruktor [CFile](#cfile) listę opcji trybu.

*Perror*<br/>
Wskaźnik do istniejącego obiektu wyjątku pliku, który otrzyma stan operacji nie powiodło się.

*Ptm*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli otwarte zakończyło się pomyślnie; w przeciwnym razie 0. Parametr *pError* ma znaczenie tylko wtedy, gdy zwracany jest 0.

### <a name="remarks"></a>Uwagi

Dwie `Open` funkcje są "bezpieczne" metody otwierania pliku, gdzie błąd jest normalnym, oczekiwanym warunkiem.

Podczas `CFile` konstruktora zgłasza wyjątek w `Open` warunku błędu, zwraca FALSE dla warunków błędu. `Open`można jeszcze zainicjować [CFileException](../../mfc/reference/cfileexception-class.md) obiektu do opisania błędu, jednak. Jeśli nie podasz parametru *pError* lub jeśli przekażesz wartość `Open` NULL dla `CFileException` *pError,* zwraca wartość FAŁSZ i nie zgłasza pliku . Jeśli przekażesz wskaźnik `CFileException`do `Open` istniejącego i napotkasz błąd, funkcja wypełnia go informacjami opisującymi ten błąd. `Open`nie zgłasza wyjątek w obu przypadkach.

W poniższej tabeli `Open`opisano możliwe wyniki gry .

|`pError`|Napotkany błąd|Wartość zwracana|Zawartość CFileException|
|--------------|------------------------|------------------|----------------------------|
|NULL|Nie|Prawda|Nie dotyczy|
|ptr do`CFileException`|Nie|Prawda|Niezmienione|
|NULL|Tak|FAŁSZ|Nie dotyczy|
|ptr do`CFileException`|Tak|FAŁSZ|zainicjowany w celu opisania błędu|

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

## <a name="cfileoperator-handle"></a><a name="operator_handle"></a>CFile::uchwyt operatora

`CFile` Ten operator służy do przekazywania dojścia do obiektu do funkcji, takich jak [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) i [GetFileTime,](/windows/win32/api/fileapi/nf-fileapi-getfiletime) które oczekują . `HANDLE`

```
operator HANDLE() const;
```

## <a name="cfileread"></a><a name="read"></a>Plik C::Odczyt

Odczytuje dane do buforu z `CFile` pliku skojarzonego z obiektem.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf (właśc.*<br/>
Wskaźnik do buforu dostarczonego przez użytkownika, który ma odbierać dane odczytane z pliku.

*Ncount*<br/>
Maksymalna liczba bajtów do odczytania z pliku. W przypadku plików w trybie tekstowym pary wiersza powrotu karetki są liczone jako pojedyncze znaki.

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów przeniesionych do buforu. Dla `CFile` wszystkich klas zwracana wartość może być mniejsza niż *nCount,* jeśli osiągnięto koniec pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

Inny przykład zobacz [CFile::Otwórz](#open).

## <a name="cfileremove"></a><a name="remove"></a>CFile::Usuń

Ta funkcja statyczna usuwa plik określony przez ścieżkę.

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Ciąg, który jest ścieżką do żądanego pliku. Ścieżka może być względna lub bezwzględna i może zawierać nazwę sieciową.

*Ptm*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

`Remove`nie spowoduje usunięcia katalogu.

Funkcja `Remove` elementu członkowskiego zgłasza wyjątek, jeśli połączony plik jest otwarty lub jeśli nie można usunąć pliku. Ta funkcja jest równoważna z poleceniem DEL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

## <a name="cfilerename"></a><a name="rename"></a>CFile::Zmień nazwę

Ta funkcja statyczna zmienia nazwę określonego pliku.

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszOldName (Nazwa)*<br/>
Stara ścieżka.

*lpszNewName*<br/>
Nowa ścieżka.

*Ptm*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

Nie można zmienić nazwy katalogów. Ta funkcja jest odpowiednikiem polecenia REN.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

## <a name="cfileseek"></a><a name="seek"></a>Plik C::Szukaj

Zmienia położenie wskaźnika pliku w otwartym pliku.

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lOff (wyjęcie*<br/>
Liczba bajtów, aby przenieść wskaźnik pliku. Wartości dodatnie przesuwają wskaźnik pliku na końcu pliku; wartości ujemne przesuwają wskaźnik pliku w kierunku początku pliku.

*nZ*<br/>
Pozycja do poszukiwania. Zobacz uwagi sekcji możliwe wartości.

### <a name="return-value"></a>Wartość zwracana

Położenie wskaźnika pliku, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie zwracana wartość jest niezdefiniowana i zgłaszany jest wskaźnik do wyjątku. `CFileException`

### <a name="remarks"></a>Uwagi

W poniższej tabeli wymieniono możliwe wartości parametru *nFrom.*

|Wartość|Opis|
|-----------|-----------------|
|`CFile::begin`|Szukaj od początku pliku.|
|`CFile::current`|Szukaj z bieżącej lokalizacji wskaźnika pliku.|
|`CFile::end`|Szukaj od końca pliku.|

Po otwarciu pliku wskaźnik pliku jest ustawiony na 0, początek pliku.

Wskaźnik pliku można ustawić na pozycję znajdującą się poza końcem pliku. Jeśli to zrobisz, rozmiar pliku nie wzrośnie, dopóki nie zapiszesz do pliku.

Program obsługi wyjątków dla tej metody musi usunąć obiekt wyjątku po przetworzeniu wyjątku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

## <a name="cfileseektobegin"></a><a name="seektobegin"></a>CFile::SeekToBegin

Ustawia wartość wskaźnika pliku na początku pliku.

```
void SeekToBegin();
```

### <a name="remarks"></a>Uwagi

`SeekToBegin()`odpowiada `Seek( 0L, CFile::begin )`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

## <a name="cfileseektoend"></a><a name="seektoend"></a>Plik C::SeekToEnd

Ustawia wartość wskaźnika pliku na logicznym końcu pliku.

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>Wartość zwracana

Długość pliku w bajtach.

### <a name="remarks"></a>Uwagi

`SeekToEnd()`odpowiada `CFile::Seek( 0L, CFile::end )`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

## <a name="cfilesetfilepath"></a><a name="setfilepath"></a>CFile::SetFilePath

Wywołanie tej funkcji, aby określić ścieżkę pliku. Na przykład jeśli ścieżka pliku nie jest dostępna, gdy [CFile](../../mfc/reference/cfile-class.md) obiekt `SetFilePath` jest skonstruowany, wywołanie, aby go dostarczyć.

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parametry

*lpszNewName*<br/>
Wskaźnik do ciągu określającego nową ścieżkę.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> `SetFilePath`nie otwiera pliku ani nie tworzy pliku; po prostu kojarzy `CFile` obiekt z nazwą ścieżki, która może być następnie użyta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

## <a name="cfilesetlength"></a><a name="setlength"></a>Plik C::SetLength

Wywołanie tej funkcji, aby zmienić długość pliku.

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>Parametry

*dwNewLen (Nienawisłe*<br/>
Żądana długość pliku w bajtach. Ta wartość może być większa lub mniejsza niż bieżąca długość pliku. Plik zostanie odpowiednio rozszerzony lub obcięty.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Z `CMemFile`, ta funkcja `CMemoryException` może rzucić obiekt.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

## <a name="cfilesetstatus"></a><a name="setstatus"></a>CFile::SetStatus

Ustawia stan pliku skojarzonego z tą lokalizacją pliku.

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Ciąg, który jest ścieżką do żądanego pliku. Ścieżka może być względna lub bezwzględna i może zawierać nazwę sieciową.

*Stan*<br/>
Bufor zawierający nowe informacje o stanie. Wywołanie `GetStatus` funkcji elementu członkowskiego, aby wstępnie wypełnić strukturę `CFileStatus` bieżącymi wartościami, a następnie wprowadzić zmiany zgodnie z wymaganiami. Jeśli wartość wynosi 0, odpowiedni element stanu nie jest aktualizowany. Zobacz [GetStatus](#getstatus) funkcji elementu członkowskiego `CFileStatus` opis struktury.

*Ptm*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

Aby ustawić godzinę, `m_mtime` zmodyfikuj pole *stanu*.

Podczas wywoływania `SetStatus` w próbie zmiany tylko atrybuty pliku, `m_mtime` a element członkowski struktury stanu pliku jest niezerowy, atrybuty mogą również mieć wpływ (zmiana sygnatury czasowej może mieć skutki uboczne dla atrybutów). Jeśli chcesz zmienić tylko atrybuty pliku, `m_mtime` najpierw ustaw element członkowski struktury stanu pliku `SetStatus`na zero, a następnie nawiąż połączenie z programem .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

## <a name="cfileunlockrange"></a><a name="unlockrange"></a>Plik C::UnlockRange

Odblokowuje zakres bajtów w otwartym pliku.

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parametry

*dwPos (właśc.*<br/>
Przesunięcie bajtu początkowego zakresu bajtów do odblokowania.

*dwCount (licz)*<br/>
Liczba bajtów w zakresie do odblokowania.

### <a name="remarks"></a>Uwagi

Zobacz opis [LockRange](#lockrange) funkcji elementu członkowskiego, aby uzyskać szczegółowe informacje.

> [!NOTE]
> Ta funkcja nie jest `CMemFile`dostępna dla klasy pochodnej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilewrite"></a><a name="write"></a>CFile::Zapis

Zapisuje dane z bufora do pliku `CFile` skojarzonego z obiektem.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf (właśc.*<br/>
Wskaźnik do buforu dostarczonego przez użytkownika, który zawiera dane, które mają być zapisywane w pliku.

*Ncount*<br/>
Liczba bajtów, które mają zostać przeniesione z buforu. W przypadku plików w trybie tekstowym pary wiersza powrotu karetki są liczone jako pojedyncze znaki.

### <a name="remarks"></a>Uwagi

`Write`zgłasza wyjątek w odpowiedzi na kilka warunków, w tym warunek pełnego dysku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

Zobacz też przykłady [CFile::CFile](#cfile) i [CFile::Open](#open).

## <a name="see-also"></a>Zobacz też

[Próbka MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CStdioFile](../../mfc/reference/cstdiofile-class.md)<br/>
[Klasa CMemFile](../../mfc/reference/cmemfile-class.md)
