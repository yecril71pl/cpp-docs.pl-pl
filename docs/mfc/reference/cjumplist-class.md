---
title: Klasa CJumpList
ms.date: 03/27/2019
f1_keywords:
- CJumpList
- AFXADV/CJumpList
- AFXADV/CJumpList::CJumpList
- AFXADV/CJumpList::AbortList
- AFXADV/CJumpList::AddDestination
- AFXADV/CJumpList::AddKnownCategory
- AFXADV/CJumpList::AddTask
- AFXADV/CJumpList::AddTasks
- AFXADV/CJumpList::AddTaskSeparator
- AFXADV/CJumpList::ClearAll
- AFXADV/CJumpList::ClearAllDestinations
- AFXADV/CJumpList::CommitList
- AFXADV/CJumpList::GetDestinationList
- AFXADV/CJumpList::GetMaxSlots
- AFXADV/CJumpList::GetRemovedItems
- AFXADV/CJumpList::InitializeList
- AFXADV/CJumpList::SetAppID
helpviewer_keywords:
- CJumpList [MFC], CJumpList
- CJumpList [MFC], AbortList
- CJumpList [MFC], AddDestination
- CJumpList [MFC], AddKnownCategory
- CJumpList [MFC], AddTask
- CJumpList [MFC], AddTasks
- CJumpList [MFC], AddTaskSeparator
- CJumpList [MFC], ClearAll
- CJumpList [MFC], ClearAllDestinations
- CJumpList [MFC], CommitList
- CJumpList [MFC], GetDestinationList
- CJumpList [MFC], GetMaxSlots
- CJumpList [MFC], GetRemovedItems
- CJumpList [MFC], InitializeList
- CJumpList [MFC], SetAppID
ms.assetid: d364d27e-f512-4b12-9872-c2a17c78ab1f
ms.openlocfilehash: 2e45e2e58bd51d36b6412940b7ed01aa119017ed
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754935"
---
# <a name="cjumplist-class"></a>Klasa CJumpList

A `CJumpList` to lista skrótów ujawniona po kliknięciu prawym przyciskiem myszy ikony na pasku zadań.

## <a name="syntax"></a>Składnia

```
class CJumpList;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Lista CJumpList::CJumpList](#cjumplist)|Konstruuje `CJumpList` obiekt.|
|[Lista CJumpList::~CJumpList](#_dtorcjumplist)|Niszczy `CJumpList` obiekt.|

|Nazwa|Opis|
|----------|-----------------|
|[Lista CJumpList::Lista przerwań](#abortlist)|Przerywa transakcję budowania listy bez zatwierdzania.|
|[Lista CJumpList::AddDestination](#adddestination)|Przeciążone. Dodaje miejsce docelowe do listy.|
|[Lista CJumpList::AddKnownCategory](#addknowncategory)|Dołącza znaną kategorię do listy.|
|[Lista CJumpList::Dodajzadę](#addtask)|Przeciążone. Dodaje elementy do kategorii Zadania kanoniczne.|
|[Lista CJumpList::Dodawanie zadań](#addtasks)|Dodaje elementy do kategorii Zadania kanoniczne.|
|[Lista CJumpList::AddTaskSeparator](#addtaskseparator)|Dodaje separator między zadaniami.|
|[Lista CJumpList::ClearAll](#clearall)|Usuwa wszystkie zadania i miejsca docelowe, które `CJumpList` zostały dodane do bieżącego wystąpienia do tej pory.|
|[Lista CJumpList::ClearAllDestinations](#clearalldestinations)|Usuwa wszystkie miejsca docelowe, które zostały `CJumpList` dodane do bieżącego wystąpienia do tej pory.|
|[Lista CJumpList::Lista zatwierdzania](#commitlist)|Kończy transakcję budowania listy i zatwierdza zgłoszoną listę do skojarzonego magazynu (rejestru w tym przypadku).|
|[Lista CJumpList::Lista wystaw](#getdestinationlist)|Pobiera wskaźnik interfejsu do listy docelowej.|
|[Lista CJumpList::GetMaxSlots](#getmaxslots)|Pobiera maksymalną liczbę elementów, w tym nagłówki kategorii, które mogą być wyświetlane w menu docelowym aplikacji wywołującej.|
|[Lista CJumpList::GetRemovedItems](#getremoveditems)|Zwraca tablicę elementów, które reprezentują usunięte miejsca docelowe.|
|[Lista CJumpList::InitializeList](#initializelist)|Rozpoczyna transakcję budowania listy.|
|[Lista CJumpList::SetAppID](#setappid)|Ustawia identyfikator modelu użytkownika aplikacji dla listy, która zostanie zbudowana.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Lista CJumplist](../../mfc/reference/cjumplist-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxadv.h

## <a name="cjumplistcjumplist"></a><a name="_dtorcjumplist"></a>Lista CJumpList::~CJumpList

Niszczy `CJumpList` obiekt.

```
~CJumpList();
```

## <a name="cjumplistabortlist"></a><a name="abortlist"></a>Lista CJumpList::Lista przerwań

Przerywa transakcję budowania listy bez zatwierdzania.

```cpp
void AbortList();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej metody ma taki `CJumpList` sam `CommitList`efekt jak zniszczenie bez wywoływania .

## <a name="cjumplistadddestination"></a><a name="adddestination"></a>Lista CJumpList::AddDestination

Dodaje miejsce docelowe do listy.

```
BOOL AddDestination(
    LPCTSTR lpcszCategoryName,
    LPCTSTR strDestinationPath);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellItem* pShellItem);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellLink* pShellLink);
```

### <a name="parameters"></a>Parametry

*lpcszCategoryName (Nazwa)*<br/>
Określa nazwę kategorii. Jeśli określona kategoria nie istnieje, zostanie utworzona.

*strDestinationPath (strDestinationPath)*<br/>
Określa plik ścieżki do pliku docelowego.

*nazwa strCategoryName*<br/>
Określa nazwę kategorii. Jeśli określona kategoria nie istnieje, zostanie utworzona.

*pShellItem (Niemkom)*<br/>
Określa element powłoki reprezentujący dodawany cel podróży.

*pShellLink (włazowanie do sieci)*<br/>
Określa łącze powłoki reprezentujące dodawany cel podróży.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Wystąpienie `CJumpList` wewnętrznie gromadzi dodane miejsca docelowe, `CommitList`a następnie zatwierdza je w .

## <a name="cjumplistaddknowncategory"></a><a name="addknowncategory"></a>Lista CJumpList::AddKnownCategory

Dołącza znaną kategorię do listy.

```
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```

### <a name="parameters"></a>Parametry

*Kategorii*<br/>
Określa znany typ kategorii. Może być KDC_RECENT lub KDC_KNOWN.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Znane kategorie są częste i ostatnie kategorie, które będziemy automatycznie `SHAddToRecentDocs` obliczać dla każdej aplikacji, która wykorzystuje (lub pośrednio używa go jako powłoki będzie go wywołać w imieniu aplikacji w niektórych scenariuszach).

## <a name="cjumplistaddtask"></a><a name="addtask"></a>Lista CJumpList::Dodajzadę

Dodaje elementy do kategorii Zadania kanoniczne.

```
BOOL AddTask(
    LPCTSTR strTargetExecutablePath,
    LPCTSTR strCommandLineArgs,
    LPCTSTR strTitle,
    LPCTSTR strIconLocation,
    int iIconIndex);

BOOL AddTask(IShellLink* pShellLink);
```

### <a name="parameters"></a>Parametry

*strTargetExecutablePath (Ścieżka celowa)*<br/>
Określa docelową ścieżkę zadania.

*strCommandLineArgs (Komant KompemdlineArgs)*<br/>
Określa argumenty wiersza polecenia pliku wykonywalnego określonego przez *strTargetExecutablePath*.

*strTitle (napis)*<br/>
Nazwa zadania, która będzie wyświetlana na liście docelowej.

*priconLokacja*<br/>
Lokalizacja ikony, która zostanie wyświetlona na liście docelowej wraz z tytułem.

*iIconIndex*<br/>
Indeks ikon.

*pShellLink (włazowanie do sieci)*<br/>
Łącze powłoki, które reprezentuje zadanie, które należy dodać.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Wystąpienie `CJumpList` gromadzi określone zadania i dodaje je `CommitList`do listy docelowych podczas . Elementy zadania pojawią się w kategorii u dołu menu docelowego aplikacji. Ta kategoria ma pierwszeństwo przed wszystkimi innymi kategoriami po wypełnieniu interfejsu użytkownika.

## <a name="cjumplistaddtasks"></a><a name="addtasks"></a>Lista CJumpList::Dodawanie zadań

Dodaje elementy do kategorii Zadania kanoniczne.

```
BOOL AddTasks(IObjectArray* pObjectCollection);
```

### <a name="parameters"></a>Parametry

*pObjectCollection (Wyliczenie poukładowe)*<br/>
Kolekcja zadań, które mają zostać dodane.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Wystąpienie CJumpList gromadzi określone zadania i dodaje je `CommitList`do listy docelowej podczas . Elementy zadania pojawią się w kategorii u dołu menu docelowego aplikacji. Ta kategoria ma pierwszeństwo przed wszystkimi innymi kategoriami po wypełnieniu interfejsu użytkownika.

## <a name="cjumplistaddtaskseparator"></a><a name="addtaskseparator"></a>Lista CJumpList::AddTaskSeparator

Dodaje separator między zadaniami.

```
BOOL AddTaskSeparator();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli to się powiedzie, 0, jeśli nie jest.

## <a name="cjumplistcjumplist"></a><a name="cjumplist"></a>Lista CJumpList::CJumpList

Konstruuje `CJumpList` obiekt.

```
CJumpList(BOOL bAutoCommit = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoCommit*<br/>
Jeśli ten parametr jest FALSE, lista nie jest automatycznie zatwierdzana w destrurze.

## <a name="cjumplistclearall"></a><a name="clearall"></a>Lista CJumpList::ClearAll

Usuwa wszystkie zadania i miejsca docelowe, które `CJumpList` zostały dodane do bieżącego wystąpienia do tej pory.

```cpp
void ClearAll();
```

### <a name="remarks"></a>Uwagi

Ta metoda czyści i zwalnia wszystkie dane i interfejsy wewnętrzne.

## <a name="cjumplistclearalldestinations"></a><a name="clearalldestinations"></a>Lista CJumpList::ClearAllDestinations

Usuwa wszystkie miejsca docelowe, które zostały dodane do bieżącego wystąpienia CJumpList do tej pory.

```cpp
void ClearAllDestinations();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, jeśli chcesz usunąć wszystkie miejsca docelowe, które zostały dodane do tej pory w bieżącej sesji budynku listy docelowej i dodać inne miejsca docelowe ponownie. Jeśli wewnętrzna `ICustomDestinationList` została zainicjowana, pozostaje żywa.

## <a name="cjumplistcommitlist"></a><a name="commitlist"></a>Lista CJumpList::Lista zatwierdzania

Kończy transakcję budowania listy i zatwierdza zgłoszoną listę do skojarzonego magazynu (rejestru w tym przypadku).

```
BOOL CommitList();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Zatwierdzenie jest atomowej. Błąd zostanie zwrócony, jeśli zatwierdzenie zakończy się niepowodzeniem.  Po `CommitList` wywołaniu bieżąca lista usuniętych elementów zostanie wyczyszczona. Wywołanie tej metody resetuje obiekt, tak aby nie ma aktywnej transakcji budowania listy. Aby zaktualizować listę, `BeginList` należy wywołać ponownie.

## <a name="cjumplistgetdestinationlist"></a><a name="getdestinationlist"></a>Lista CJumpList::Lista wystaw

Pobiera wskaźnik interfejsu do listy docelowej.

```
ICustomDestinationList* GetDestinationList();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Jeśli lista szybkiego dostępu nie została zainicjowana lub została zatwierdzona lub przerwana, zwrócona wartość będzie null.

## <a name="cjumplistgetmaxslots"></a><a name="getmaxslots"></a>Lista CJumpList::GetMaxSlots

Pobiera maksymalną liczbę elementów, w tym nagłówki kategorii, które mogą być wyświetlane w menu docelowym aplikacji wywołującej.

```
UINT GetMaxSlots() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Aplikacje mogą zgłaszać tylko liczbę elementów i nagłówki kategorii połączone do tej wartości. Jeśli `AppendCategory`wywołania `AppendKnownCategory`, `AddUserTasks` , lub przekroczyć ten numer, będą zwracać błąd.

## <a name="cjumplistgetremoveditems"></a><a name="getremoveditems"></a>Lista CJumpList::GetRemovedItems

Zwraca tablicę elementów, które reprezentują usunięte miejsca docelowe.

```
IObjectArray* GetRemovedItems();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Usunięte miejsca docelowe są pobierane podczas inicjowania listy szybkiego dostępu. Podczas generowania nowej listy docelowej aplikacje powinny najpierw przetworzyć listę usuniętych miejsc docelowych, czyszcząc swoje dane śledzenia dla dowolnego elementu zwróconego przez wyliczacz usuniętej listy. Jeśli aplikacja próbuje podać element, który został właśnie usunięty w `BeginList` transakcji, że bieżące wywołanie rozpoczęte, wywołanie metody, która ponownie dodał, że element zakończy się niepowodzeniem, aby upewnić się, że aplikacje są zgodne z listę usuniętych.

## <a name="cjumplistinitializelist"></a><a name="initializelist"></a>Lista CJumpList::InitializeList

Rozpoczyna transakcję budowania listy.

```
BOOL InitializeList();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Nie trzeba wywoływać tej metody jawnie, chyba że chcesz `ICustomDestinationList` `GetDestinationList`pobrać wskaźnik do korzystania, `GetMaxSlots`liczbę dostępnych gniazd `GetRemovedItems`przy użyciu lub listę usuniętych elementów za pomocą .

## <a name="cjumplistsetappid"></a><a name="setappid"></a>Lista CJumpList::SetAppID

Ustawia identyfikator modelu użytkownika aplikacji dla listy, która zostanie zbudowana.

```cpp
void SetAppID(LPCTSTR strAppID);
```

### <a name="parameters"></a>Parametry

*strAppID (ul.*<br/>
Ciąg określający identyfikator modelu użytkownika aplikacji.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
