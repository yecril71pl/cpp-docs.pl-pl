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
ms.openlocfilehash: a258773633f503dc0638d76509953b3410dafbd8
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375760"
---
# <a name="cfile-class"></a>Klasa CFile

Klasa bazowa klas plików klas Microsoft Foundation.

## <a name="syntax"></a>Składnia

```
class CFile : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFile::CFile](#cfile)|Konstruuje `CFile` obiekt ze ścieżki lub dojścia do pliku.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFile:: Abort](#abort)|Zamyka plik, ignorując wszystkie ostrzeżenia i błędy.|
|[CFile:: Close](#close)|Zamyka plik i usuwa obiekt.|
|[CFile::Duplicate](#duplicate)|Tworzy zduplikowany obiekt na podstawie tego pliku.|
|[CFile:: Flush](#flush)|Opróżnia wszystkie dane, które mają być zapisywane.|
|[CFile::GetFileName](#getfilename)|Pobiera nazwę pliku wybranego.|
|[CFile::GetFilePath](#getfilepath)|Pobiera pełną ścieżkę pliku wybranego pliku.|
|[CFile::GetFileTitle](#getfiletitle)|Pobiera tytuł wybranego pliku.|
|[CFile:: GetLength](#getlength)|Pobiera długość pliku.|
|[CFile:: GetPosition](#getposition)|Pobiera bieżący wskaźnik pliku.|
|[CFile:: GetStatus](#getstatus)|Pobiera stan otwartego pliku lub w wersji statycznej, Pobiera stan określonego pliku (statyczna, funkcja wirtualna).|
|[CFile::LockRange](#lockrange)|Blokuje zakres bajtów w pliku.|
|[CFile:: Open](#open)|Bezpiecznie otwiera plik z opcją testowania błędów.|
|[CFile:: Read](#read)|Odczytuje (niebuforowane) dane z pliku w bieżącym położeniu.|
|[CFile:: Remove](#remove)|Usuwa określony plik (funkcja statyczna).|
|[CFile:: Rename](#rename)|Zmienia nazwę określonego pliku (funkcja statyczna).|
|[CFile::Seek](#seek)|Określa położenie bieżącego wskaźnika pliku.|
|[CFile::SeekToBegin](#seektobegin)|Ustawia bieżący wskaźnik pliku na początku pliku.|
|[CFile::SeekToEnd](#seektoend)|Ustawia bieżący wskaźnik pliku na końcu pliku.|
|[CFile::SetFilePath](#setfilepath)|Ustawia pełną ścieżkę pliku dla wybranego pliku.|
|[CFile:: SetLength](#setlength)|Zmienia długość pliku.|
|[CFile:: SetStatus](#setstatus)|Ustawia stan określonego pliku (statyczna, wirtualna funkcja).|
|[CFile::UnlockRange](#unlockrange)|Odblokowuje zakres bajtów w pliku.|
|[CFile:: Write](#write)|Zapisuje (niebuforowane) dane w pliku do bieżącego położenia pliku.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFile:: uchwyt operatora](#operator_handle)|Dojście do `CFile` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CFile::hFileNull](#hfilenull)|Określa, `CFile` czy obiekt ma prawidłowe dojście.|
|[CFile::m_hFile](#m_hfile)|Zwykle zawiera dojście do pliku systemu operacyjnego.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CFile::m_pTM](#m_ptm)|Wskaźnik do `CAtlTransactionManager` obiektu.|

## <a name="remarks"></a>Uwagi

Zapewnia bezpośrednią pamięć podbuforowaną, dane wejściowe/wyjściowe na dyskach binarnych i pośrednio obsługuje pliki tekstowe i pliki pamięci za poorednictwem klas pochodnych. `CFile`działa w połączeniu z `CArchive` klasą do obsługi serializacji obiektów klasy Microsoft Foundation.

Hierarchiczna relacja między tą klasą i jej klasami pochodnymi umożliwia programowi wykonywanie operacji na wszystkich obiektach plików za pomocą interfejsu polimorficznego `CFile` . Plik pamięci, na przykład, zachowuje się jak plik dysku.

Użyj `CFile` i jej klas pochodnych dla operacji we/wy dysku ogólnego przeznaczenia. Użyj `ofstream` lub innych klas `iostream` firmy Microsoft dla sformatowanego tekstu wysyłanego do pliku dyskowego.

Zwykle plik dyskowy jest otwierany automatycznie podczas `CFile` budowania i zamykany podczas niszczenia. Statyczne funkcje Członkowskie umożliwiają przejrzeć stanu pliku bez otwierania pliku.

Aby uzyskać więcej informacji na `CFile`temat korzystania z programu, zapoznaj się z artykułami [pliki w bibliotece MFC](../../mfc/files-in-mfc.md) i [Obsługa plików](../../c-runtime-library/file-handling.md) w *dokumentacji dotyczącej biblioteki wykonawczej*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="abort"></a>CFile:: Abort

Zamyka plik skojarzony z tym obiektem i sprawia, że plik jest niedostępny do odczytu lub zapisu.

```
virtual void Abort();
```

### <a name="remarks"></a>Uwagi

Jeśli plik nie został zamknięty przed zniszczeniem obiektu, destruktor zamknie go.

Obsługa wyjątków `CFile::Abort` różni się od `CFile::Close` na dwa sposoby. Najpierw funkcja nie zgłosi wyjątku w przypadku błędów, ponieważ błędy są ignorowane przez `Abort`. `Abort` **Jeśli plik** nie został otwarty lub został wcześniej zamknięty, niezostaniezaakceptowany.`Abort`

Jeśli użyto **nowej** do przydzielenia `CFile` obiektu na stercie, należy usunąć go po zamknięciu pliku. `Abort`ustawia `m_hFile` jako `CFile::hFileNull`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

##  <a name="cfile"></a>CFile:: CFile

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

*hFile*<br/>
Dojście pliku do dołączenia do `CFile` obiektu.

*lpszFileName*<br/>
Względna lub pełna ścieżka pliku do dołączenia do `CFile` obiektu.

*nOpenFlags*<br/>
Kombinacja bitowa (lub) opcji dostępu do pliku dla określonego pliku. Zobacz sekcję Uwagi, aby poznać możliwe opcje.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

W poniższych pięciu tabelach przedstawiono możliwe opcje parametru *nOpenFlags* .

Wybierz tylko jedną z następujących opcji trybu dostępu do pliku. Domyślny tryb dostępu do pliku to `CFile::modeRead`, który jest tylko do odczytu.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::modeRead`|Żąda dostępu tylko do odczytu.|
|`CFile::modeWrite`|Żądania dostępu tylko do zapisu.|
|`CFile::modeReadWrite`|Żąda dostępu do odczytu i zapisu.|

Wybierz jedną z następujących opcji trybu znakowego.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::typeBinary`|Ustawia tryb binarny (używany tylko w klasach pochodnych).|
|`CFile::typeText`|Ustawia tryb tekstowy ze specjalnym przetwarzaniem par wysuwu wiersza powrotu karetki (używane tylko w klasach pochodnych).|
|`CFile::typeUnicode`|Ustawia tryb Unicode (używany tylko w klasach pochodnych). Tekst jest zapisywana w pliku w formacie Unicode, gdy aplikacja jest wbudowana w konfigurację Unicode. W pliku nie zapisano BOM.|

Wybierz tylko jedną z następujących opcji trybu udostępniania plików. Domyślny tryb udziału plików to `CFile::shareExclusive`, który jest na wyłączność.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::shareDenyNone`|Brak ograniczeń udostępniania.|
|`CFile::shareDenyRead`|Odmowa dostępu do odczytu dla wszystkich innych użytkowników.|
|`CFile::shareDenyWrite`|Odmawia dostępu do zapisu innym osobom.|
|`CFile::shareExclusive`|Odmawia dostępu do odczytu i zapisu dla wszystkich innych użytkowników.|

Wybierz pierwszy lub oba te opcje trybu tworzenia pliku. Domyślny tryb tworzenia to `CFile::modeNoTruncate`, który jest otwarty istniejące.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::modeCreate`|Tworzy nowy plik, jeśli plik nie istnieje. Jeśli plik już istnieje, zostanie nadpisany i początkowo ustawiony na zerową długość.|
|`CFile::modeNoTruncate`|Tworzy nowy plik, jeśli plik nie istnieje; w przeciwnym razie, jeśli plik już istnieje, jest dołączony do `CFile` obiektu.|

Wybierz poniższe opcje buforowania plików zgodnie z opisem. Domyślnie system używa schematu buforowania ogólnego przeznaczenia, który nie jest dostępny jako opcja.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::osNoBuffer`|System nie używa pośredniej pamięci podręcznej dla tego pliku. Ta opcja powoduje anulowanie następujących 2 opcji.|
|`CFile::osRandomAccess`|Pamięć podręczna plików jest zoptymalizowana pod kątem dostępu losowego. Nie należy używać obu tych opcji i opcji skanowania sekwencyjnego.|
|`CFile::osSequentialScan`|Pamięć podręczna plików jest zoptymalizowana pod kątem dostępu sekwencyjnego. Nie używaj tej opcji i opcji dostępu swobodnego.|
|`CFile::osWriteThrough`|Operacje zapisu są wykonywane bez opóźnień.|

Aby zapobiec dziedziczeniu dojścia do pliku, wybierz następującą opcję zabezpieczeń. Domyślnie wszystkie nowe procesy podrzędne mogą korzystać z dojścia do pliku.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::modeNoInherit`|Uniemożliwia procesom podrzędnym korzystanie z dojścia do pliku.|

Konstruktor domyślny inicjuje członków, ale nie dołącza pliku do `CFile` obiektu. Po użyciu tego konstruktora Użyj metody [CFile:: Open](#open) , aby otworzyć plik i dołączyć go do `CFile` obiektu.

Konstruktor z jednym parametrem inicjuje członków i dołącza istniejący plik do `CFile` obiektu.

Konstruktor z dwoma parametrami inicjuje członków i próbuje otworzyć określony plik. Jeśli ten Konstruktor pomyślnie otworzy określony plik, plik zostanie dołączony do `CFile` obiektu; w przeciwnym razie ten konstruktor zgłosi wskaźnik `CInvalidArgException` do obiektu. Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [wyjątki](../../mfc/exception-handling-in-mfc.md).

Jeśli obiekt pomyślnie otworzy określony plik, zamknie ten plik automatycznie, `CFile` gdy obiekt zostanie zniszczony; w przeciwnym razie musisz jawnie zamknąć ten plik, gdy `CFile` nie jest już dołączony do obiektu. `CFile`

### <a name="example"></a>Przykład

Poniższy kod pokazuje, `CFile`jak używać.

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

##  <a name="close"></a>CFile:: Close

Zamyka plik skojarzony z tym obiektem i sprawia, że plik jest niedostępny do odczytu lub zapisu.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Jeśli plik nie został zamknięty przed zniszczeniem obiektu, destruktor zamknie go.

Jeśli użyto **nowej** do przydzielenia `CFile` obiektu na stercie, należy usunąć go po zamknięciu pliku. `Close`ustawia `m_hFile` jako `CFile::hFileNull`.

### <a name="example"></a>Przykład

Zobacz przykład dla [CFile:: CFile](#cfile).

##  <a name="duplicate"></a>  CFile::Duplicate

Tworzy zduplikowany `CFile` obiekt dla danego pliku.

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do zduplikowanego `CFile` obiektu.

### <a name="remarks"></a>Uwagi

Ta funkcja jest równoważna z funkcją `_dup`C Run-Time.

##  <a name="flush"></a>CFile:: Flush

Wymusza, aby wszystkie pozostałe dane w buforze plików były zapisywane do pliku.

```
virtual void Flush();
```

### <a name="remarks"></a>Uwagi

Użycie `Flush` nie gwarantuje `CArchive` opróżniania buforów. Jeśli używasz archiwum, najpierw Wywołaj [CArchive:: Flush](../../mfc/reference/carchive-class.md#flush) .

### <a name="example"></a>Przykład

Zobacz przykład dla [CFile:: SetFilePath](#setfilepath).

##  <a name="getfilename"></a>CFile:: GetFileName

Wywołaj tę funkcję elementu członkowskiego, aby pobrać nazwę określonego pliku.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa pliku.

### <a name="remarks"></a>Uwagi

Na przykład po wywołaniu `GetFileName` w celu wygenerowania komunikatu o pliku `c:\windows\write\myfile.wri`zostanie zwrócona nazwa pliku `myfile.wri`,.

Aby zwrócić całą ścieżkę pliku, w tym nazwę, wywołaj metodę [GetFilePath](#getfilepath). Aby zwrócić tytuł pliku ( `myfile`), wywołaj [GetFileTitle](#getfiletitle).

### <a name="example"></a>Przykład

Ten fragment kodu otwiera SYSTEM. Plik INI w katalogu systemu WINDOWS. W przypadku znalezienia przykładu zostanie wyświetlona nazwa i ścieżka oraz tytuł, jak pokazano w obszarze Wyjście:

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

##  <a name="getfilepath"></a>CFile:: GetFilePath

Wywołaj tę funkcję elementu członkowskiego, aby pobrać pełną ścieżkę do określonego pliku.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Wartość zwracana

Pełna ścieżka określonego pliku.

### <a name="remarks"></a>Uwagi

Na przykład po wywołaniu `GetFilePath` w celu wygenerowania komunikatu dotyczącego pliku `c:\windows\write\myfile.wri`zostanie zwrócona ścieżka `c:\windows\write\myfile.wri`do pliku.

Aby zwrócić tylko nazwę pliku (`myfile.wri`), wywołaj GetFileName. [](#getfilename) Aby zwrócić tytuł pliku (`myfile`), wywołaj [GetFileTitle](#getfiletitle).

### <a name="example"></a>Przykład

Zobacz przykład dla elementu [](#getfilename)GetFileName.

##  <a name="getfiletitle"></a>CFile:: GetFileTitle

Wywołaj tę funkcję elementu członkowskiego, aby pobrać tytuł pliku (nazwa wyświetlana) dla tego pliku.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Wartość zwracana

Tytuł pliku źródłowego.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [GetFileTitle](/windows/desktop/api/commdlg/nf-commdlg-getfiletitlea) , aby pobrać tytuł pliku. Jeśli to się powiedzie, metoda zwraca ciąg używany przez system do wyświetlania nazwy pliku użytkownikowi. W przeciwnym razie metoda wywołuje [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) , aby pobrać nazwę pliku (łącznie z rozszerzeniem pliku) pliku źródłowego. Oznacza to, że rozszerzenie pliku nie jest zawsze uwzględniane w ciągu tytułu zwróconego pliku. Aby uzyskać więcej informacji, zobacz [GetFileTitle](/windows/desktop/api/commdlg/nf-commdlg-getfiletitlea) i [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) w Windows SDK.

Aby zwrócić całą ścieżkę pliku, w tym nazwę, wywołaj metodę [GetFilePath](#getfilepath). Aby zwrócić tylko nazwę pliku, wywołaj GetFileName. [](#getfilename)

### <a name="example"></a>Przykład

Zobacz przykład dla elementu [](#getfilename)GetFileName.

##  <a name="getlength"></a>CFile:: GetLength

Uzyskuje bieżącą długość logiczną pliku w bajtach.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

##  <a name="getposition"></a>CFile:: GetPosition

Uzyskuje bieżącą wartość wskaźnika pliku, która może być używana w późniejszych wywołaniach do `Seek`.

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

##  <a name="getstatus"></a>CFile:: GetStatus

Ta metoda pobiera informacje o stanie powiązane z danym `CFile` wystąpieniem obiektu lub z daną ścieżką do pliku.

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*rStatus*<br/>
Odwołanie do struktury dostarczonej `CFileStatus` przez użytkownika, która będzie otrzymywać informacje o stanie. `CFileStatus` Struktura zawiera następujące pola:

- `CTime m_ctime`Data i godzina utworzenia pliku.

- `CTime m_mtime`Data i godzina ostatniej modyfikacji pliku.

- `CTime m_atime`Data i godzina ostatniego dostępu do pliku.

- `ULONGLONG m_size`Rozmiar logiczny pliku w bajtach, który został zgłoszony przez polecenie DIR.

- `BYTE m_attribute`Bajt atrybutu pliku.

- `char m_szFullName[_MAX_PATH]`Bezwzględna nazwa pliku w zestawie znaków systemu Windows.

*lpszFileName*<br/>
Ciąg w zestawie znaków systemu Windows, który jest ścieżką do żądanego pliku. Ścieżka może być względna lub bezwzględna lub może zawierać nazwę ścieżki sieciowej.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli informacje o stanie określonego pliku zostaną pomyślnie pobrane. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Niestatyczna wersja programu `GetStatus` pobiera informacje o stanie otwartego pliku skojarzone z danym `CFile` obiektem.  Wersja statyczna programu `GetStatus` uzyskuje stan pliku z danej ścieżki pliku bez faktycznego otwierania pliku. Ta wersja jest przydatna do testowania praw dostępu do pliku.

`m_attribute` Element członkowski`CFileStatus` struktury odwołuje się do zestawu atrybutów pliku. Klasa zawiera typ wyliczeniowy atrybutu, więc atrybuty pliku można określić symbolicznie:  `CFile`

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

##  <a name="hfilenull"></a>  CFile::hFileNull

Określa obecność prawidłowego dojścia do pliku dla `CFile` obiektu.

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>Uwagi

Ta stała służy do określenia, `CFile` czy obiekt ma prawidłowe dojście do pliku.

Poniższy przykład ilustruje tę operację:

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

##  <a name="lockrange"></a>CFile:: LockRange

Blokuje zakres bajtów w otwartym pliku, zwracając wyjątek, jeśli plik jest już zablokowany.

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parametry

*dwPos*<br/>
Przesunięcie bajtów początku zakresu bajtów do zablokowania.

*dwCount*<br/>
Liczba bajtów w zakresie do zablokowania.

### <a name="remarks"></a>Uwagi

Zablokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Można zablokować więcej niż jeden region pliku, ale nie są dozwolone żadne nakładające się regiony.

Po odblokowaniu regionu przy użyciu `UnlockRange` funkcji członkowskiej zakres bajtów musi dokładnie odpowiadać regionowi, który został wcześniej zablokowany. `LockRange` Funkcja nie scala sąsiadujących regionów. Jeśli dwa zablokowane regiony są sąsiadujące, należy odblokować każdy region osobno.

> [!NOTE]
>  Ta funkcja jest niedostępna `CMemFile`dla klasy pochodnej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="m_hfile"></a>  CFile::m_hFile

Zawiera dojście do pliku systemu operacyjnego dla otwartego pliku.

```
HANDLE m_hFile;
```

### <a name="remarks"></a>Uwagi

`m_hFile`jest publiczną zmienną typu UINT. Zawiera `CFile::hFileNull`ona niezależny od systemu operacyjnego wskaźnik pustego pliku, jeśli dojście nie zostało przypisane.

`m_hFile` Użycie nie jest zalecane, ponieważ znaczenie elementu członkowskiego zależy od klasy pochodnej. `m_hFile`jest członkiem publicznej składowej dla wygody obsługi niepolimorficznego użycia klasy.

##  <a name="m_ptm"></a>  CFile::m_pTM

Wskaźnik do `CAtlTransactionManager` obiektu.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Uwagi

##  <a name="open"></a>CFile:: Open

Przeciążone. `Open`jest przeznaczony do użytku z konstruktorem `CFile` domyślnym.

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
Ciąg, który zawiera ścieżkę do żądanego pliku. Ścieżka może być względna, bezwzględna lub nazwą sieciową (UNC).

*nOpenFlags*<br/>
Element UINT, który definiuje tryb udostępniania i dostępu do pliku. Określa akcję do wykonania podczas otwierania pliku. Opcje można łączyć za pomocą operatora bitowego lub ( **&#124;** ). Wymagane są jedno uprawnienie dostępu i jedna opcja udostępniania; tryby `modeCreate` i`modeNoInherit` są opcjonalne. Zapoznaj się z listą opcji trybu w konstruktorze [CFile](#cfile) .

*pError*<br/>
Wskaźnik do istniejącego obiektu wyjątku pliku, który otrzyma stan operacji zakończonej niepowodzeniem.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli otwarcie zakończyło się pomyślnie; w przeciwnym razie 0. Parametr *pError* ma znaczenie tylko wtedy, gdy zwracana jest wartość 0.

### <a name="remarks"></a>Uwagi

Te dwie `Open` funkcje są "bezpiecznymi" metodami otwierania plików, w których wystąpił błąd normalny, oczekiwany warunek.

Chociaż Konstruktor zgłasza wyjątek w warunku błędu, `Open` zwraca wartość false dla warunków błędu. `CFile` `Open`może jednak nadal inicjować obiekt [CFileException](../../mfc/reference/cfileexception-class.md) w celu opisywania błędu. Jeśli nie podasz parametru *pError* lub Jeśli przekażesz wartość null dla *pError*, `Open` zwraca wartość false i nie generuje elementu `CFileException`. Jeśli przekażesz wskaźnik do istniejącej `CFileException`i `Open` napotkasz błąd, funkcja wypełni ją informacjami opisującymi ten błąd. `Open`nie zgłasza wyjątku w obu przypadkach.

W poniższej tabeli opisano możliwe wyniki działania programu `Open`.

|`pError`|Wystąpił błąd|Wartość zwracana|Zawartość CFileException|
|--------------|------------------------|------------------|----------------------------|
|NULL|Nie|OZNACZA|n/d|
|PTR na`CFileException`|Nie|OZNACZA|bez zmian|
|NULL|Yes|FAŁSZ|n/d|
|PTR na`CFileException`|Tak|FAŁSZ|zainicjowany do opisywania błędu|

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

##  <a name="operator_handle"></a>CFile:: uchwyt operatora

Użyj tego operatora, aby przekazać dojście do `CFile` obiektu do funkcji, takich jak [ReadFileEx](/windows/desktop/api/fileapi/nf-fileapi-readfileex) i [GetFileTime](/windows/desktop/api/fileapi/nf-fileapi-getfiletime) , które `HANDLE`oczekują.

```
operator HANDLE() const;
```

##  <a name="read"></a>CFile:: Read

Odczytuje dane do buforu z pliku skojarzonego z `CFile` obiektem.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Wskaźnik do buforu dostarczonego przez użytkownika, który ma otrzymywać dane odczytane z pliku.

*nCount*<br/>
Maksymalna liczba bajtów, które mają być odczytywane z pliku. W przypadku plików w trybie tekstowym pary wierszy powrotu karetki są zliczane jako pojedyncze znaki.

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów przesłanych do buforu. Dla wszystkich `CFile` klas zwracana wartość może być mniejsza niż *nCount* , jeśli osiągnięto koniec pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

Aby uzyskać inny przykład, zobacz [CFile:: Open](#open).

##  <a name="remove"></a>CFile:: Remove

Ta funkcja statyczna usuwa plik określony przez ścieżkę.

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Ciąg, który jest ścieżką do żądanego pliku. Ścieżka może być względna lub bezwzględna i może zawierać nazwę sieci.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

`Remove`nie można usunąć katalogu.

Funkcja `Remove` członkowska zgłasza wyjątek, jeśli połączony plik jest otwarty lub nie można usunąć pliku. Ta funkcja jest równoważna z DEL polecenie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

##  <a name="rename"></a>CFile:: Rename

Ta funkcja statyczna zmienia nazwę określonego pliku.

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszOldName*<br/>
Stara ścieżka.

*lpszNewName*<br/>
Nowa ścieżka.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

Nie można zmienić nazwy katalogów. Ta funkcja jest równoważna z poleceniem REN.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

##  <a name="seek"></a>CFile:: Seek

Zmienia położenie wskaźnika pliku w otwartym pliku.

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lOff*<br/>
Liczba bajtów do przeniesienia wskaźnika pliku. Wartości dodatnie przesuwają wskaźnik pliku do końca pliku; wartości ujemne przesuwają wskaźnik pliku do początku pliku.

*nFrom*<br/>
Pozycja do wyszukania. Więcej wartości można znaleźć w sekcji uwagi.

### <a name="return-value"></a>Wartość zwracana

Pozycja wskaźnika pliku, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie zwracana wartość jest niezdefiniowana i zostanie zgłoszony wskaźnik `CFileException` do wyjątku.

### <a name="remarks"></a>Uwagi

Poniższa tabela zawiera listę możliwych wartości parametru *NZE* .

|Wartość|Opis|
|-----------|-----------------|
|`CFile::begin`|Wyszukaj od początku pliku.|
|`CFile::current`|Wyszukaj w bieżącej lokalizacji wskaźnika pliku.|
|`CFile::end`|Wyszukaj od końca pliku.|

Gdy plik zostanie otwarty, wskaźnik pliku jest umieszczony na 0, na początku pliku.

Można ustawić wskaźnik pliku na pozycję poza końcem pliku. Jeśli to zrobisz, rozmiar pliku nie zostanie zwiększony do momentu zapisu w pliku.

Program obsługi wyjątków dla tej metody musi usunąć obiekt wyjątku po przetworzeniu wyjątku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

##  <a name="seektobegin"></a>CFile:: SeekToBegin

Ustawia wartość wskaźnika pliku na początku pliku.

```
void SeekToBegin();
```

### <a name="remarks"></a>Uwagi

`SeekToBegin()`jest odpowiednikiem `Seek( 0L, CFile::begin )`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="seektoend"></a>CFile:: SeekToEnd

Ustawia wartość wskaźnika pliku na logiczny koniec pliku.

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>Wartość zwracana

Długość pliku w bajtach.

### <a name="remarks"></a>Uwagi

`SeekToEnd()`jest odpowiednikiem `CFile::Seek( 0L, CFile::end )`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="setfilepath"></a>CFile:: SetFilePath

Wywołaj tę funkcję, aby określić ścieżkę pliku. Na przykład jeśli ścieżka pliku nie jest dostępna w przypadku konstruowania obiektu [CFile](../../mfc/reference/cfile-class.md) , należy wywołać `SetFilePath` go.

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parametry

*lpszNewName*<br/>
Wskaźnik na ciąg określający nową ścieżkę.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> `SetFilePath`nie otwiera pliku ani nie tworzy pliku; po prostu kojarzy `CFile` obiekt z nazwą ścieżki, której można następnie użyć.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

##  <a name="setlength"></a>CFile:: SetLength

Wywołaj tę funkcję, aby zmienić długość pliku.

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>Parametry

*dwNewLen*<br/>
Wymagana długość pliku w bajtach. Ta wartość może być większa lub mniejsza niż bieżąca długość pliku. Plik zostanie rozszerzony lub obcięty zgodnie z potrzebami.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  W `CMemFile`programie ta funkcja może `CMemoryException` zgłosić obiekt.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

##  <a name="setstatus"></a>CFile:: SetStatus

Ustawia stan pliku skojarzonego z tą lokalizacją pliku.

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Ciąg, który jest ścieżką do żądanego pliku. Ścieżka może być względna lub bezwzględna i może zawierać nazwę sieci.

*status*<br/>
Bufor zawierający nowe informacje o stanie. Wywołaj funkcję `CFileStatus` `GetStatus` członkowską, aby wstępnie wypełnić strukturę wartościami bieżącymi, a następnie wprowadź zmiany zgodnie z potrzebami. Jeśli wartość wynosi 0, odpowiadający jej element status nie zostanie zaktualizowany. Zapoznaj [](#getstatus) się z funkcją elementu członkowskiego GetStatus, `CFileStatus` aby zapoznać się z opisem struktury.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

Aby ustawić godzinę, zmodyfikuj `m_mtime` pole *stanu*.

W przypadku wywołania do `SetStatus` programu przy próbie zmiany tylko atrybutów pliku, `m_mtime` a element członkowski struktury stanu pliku jest różny od zera, może to mieć wpływ na atrybuty (zmiana sygnatury czasowej może mieć wpływ na atrybuty). Jeśli chcesz zmienić tylko atrybuty pliku, najpierw ustaw `m_mtime` element członkowski struktury stanu pliku na zero, a następnie wykonaj `SetStatus`wywołanie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

##  <a name="unlockrange"></a>CFile:: UnlockRange

Odblokowuje zakres bajtów w otwartym pliku.

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parametry

*dwPos*<br/>
Przesunięcie bajtu początku zakresu bajtów do odblokowania.

*dwCount*<br/>
Liczba bajtów w zakresie do odblokowania.

### <a name="remarks"></a>Uwagi

Zobacz opis funkcji elementu członkowskiego [LockRange](#lockrange) , aby uzyskać szczegółowe informacje.

> [!NOTE]
>  Ta funkcja jest niedostępna dla `CMemFile`klasy pochodnej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="write"></a>CFile:: Write

Zapisuje dane z buforu do pliku skojarzonego z `CFile` obiektem.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Wskaźnik do buforu dostarczonego przez użytkownika, który zawiera dane, które mają być zapisywane do pliku.

*nCount*<br/>
Liczba bajtów, które mają zostać przeniesione z bufora. W przypadku plików w trybie tekstowym pary wierszy powrotu karetki są zliczane jako pojedyncze znaki.

### <a name="remarks"></a>Uwagi

`Write`zgłasza wyjątek w odpowiedzi na kilka warunków, w tym dysk — pełen warunek.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

Zobacz również przykłady dla [CFile:: CFile](#cfile) i [CFile:: Open](#open).

## <a name="see-also"></a>Zobacz także

[Przykład DRAWCLI MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CStdioFile](../../mfc/reference/cstdiofile-class.md)<br/>
[Klasa CMemFile](../../mfc/reference/cmemfile-class.md)
