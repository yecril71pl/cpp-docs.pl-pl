---
title: Klasa CJumpList | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 518712dd4d52673ad88dffc0ffa76c9e0281642a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071878"
---
# <a name="cjumplist-class"></a>Klasa CJumpList

Element `CJumpList` znajduje się lista skrótów wyświetlona po kliknięciu prawym przyciskiem myszy ikonę na pasku zadań.

## <a name="syntax"></a>Składnia

```
class CJumpList;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CJumpList::CJumpList](#cjumplist)|Konstruuje `CJumpList` obiektu.|
|[CJumpList:: ~ CJumpList](#cjumplist__~cjumplist)|Niszczy `CJumpList` obiektu.|

|Nazwa|Opis|
|----------|-----------------|
|[CJumpList::AbortList](#abortlist)|Przerywa transakcję tworzenia listy bez zobowiązania.|
|[CJumpList::AddDestination](#adddestination)|Przeciążone. Dodaje miejsce docelowe do listy.|
|[CJumpList::AddKnownCategory](#addknowncategory)|Dołącza znane kategorię do listy.|
|[CJumpList::AddTask](#addtask)|Przeciążone. Dodaje elementy do canonical kategorii zadań.|
|[CJumpList::AddTasks](#addtasks)|Dodaje elementy do canonical kategorii zadań.|
|[CJumpList::AddTaskSeparator](#addtaskseparator)|Dodaje separator między zadaniami.|
|[CJumpList::ClearAll](#clearall)|Usuwa wszystkie zadania i miejsc docelowych, które zostały dodane do bieżącego wystąpienia `CJumpList` do tej pory.|
|[CJumpList::ClearAllDestinations](#clearalldestinations)|Usuwa wszystkich miejsc docelowych, które zostały dodane do bieżącego wystąpienia `CJumpList` do tej pory.|
|[CJumpList::CommitList](#commitlist)|Kończy się tworzenie listy transakcji i zatwierdzeń lista zgłoszonych do skojarzonego magazynu (rejestr w tym przypadku.)|
|[CJumpList::GetDestinationList](#getdestinationlist)|Pobiera wskaźnik interfejsu do listy docelowej.|
|[CJumpList::GetMaxSlots](#getmaxslots)|Pobiera maksymalną liczbę elementów, w tym nagłówki kategorii, które można wyświetlić w menu docelowej aplikacji wywołującej.|
|[CJumpList::GetRemovedItems](#getremoveditems)|Zwraca tablicę elementów, które reprezentują usunięte miejsc docelowych.|
|[CJumpList::InitializeList](#initializelist)|Rozpoczyna się transakcja tworzenia listy.|
|[CJumpList::SetAppID](#setappid)|Określa identyfikator modelu użytkownika aplikacji dla listy, który zostanie skompilowany.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CJumpList](../../mfc/reference/cjumplist-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxadv.h

##  <a name="_dtorcjumplist"></a>  CJumpList:: ~ CJumpList

Niszczy `CJumpList` obiektu.

```
~CJumpList();
```

##  <a name="abortlist"></a>  CJumpList::AbortList

Przerywa transakcję tworzenia listy bez zobowiązania.

```
void AbortList();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej metody ma taki sam skutek jak niszczenie `CJumpList` bez wywoływania `CommitList`.

##  <a name="adddestination"></a>  CJumpList::AddDestination

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

*lpcszCategoryName*<br/>
Określa nazwę kategorii. Określona kategoria nie istnieje, zostanie utworzony.

*strDestinationPath*<br/>
Określa ścieżkę do pliku docelowego.

*strCategoryName*<br/>
Określa nazwę kategorii. Określona kategoria nie istnieje, zostanie utworzony.

*pShellItem*<br/>
Określa element powłoki, reprezentujący docelowego dodawany.

*pShellLink*<br/>
Określa łącze powłoki reprezentujący docelowego dodawany.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Wystąpienie `CJumpList` wewnętrznie gromadzi dodano miejsc docelowych, a następnie zatwierdza je w `CommitList`.

##  <a name="addknowncategory"></a>  CJumpList::AddKnownCategory

Dołącza znane kategorię do listy.

```
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```

### <a name="parameters"></a>Parametry

*category*<br/>
Określa typ znany kategorii. Może być KDC_RECENT lub KDC_KNOWN.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Znane są kategorie częste i ostatnio używane, które firma Microsoft automatycznie oblicza dla każdej aplikacji korzystającej z typu `SHAddToRecentDocs` (lub pośrednio używa, zgodnie z powłoki programu będzie go wywoływać w imieniu aplikacji, w niektórych scenariuszach).

##  <a name="addtask"></a>  CJumpList::AddTask

Dodaje elementy do canonical kategorii zadań.

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

*strTargetExecutablePath*<br/>
Określa ścieżkę docelową zadania.

*strCommandLineArgs*<br/>
Określa argumenty wiersza polecenia pliku wykonywalnego, określony przez strTargetExecutablePath.

*strTitle*<br/>
Nazwa zadania, która będzie wyświetlana na liście docelowego.

*strIconLocation*<br/>
Lokalizacja ikony, która będzie wyświetlana na liście docelowy wraz z tytułem.

*iIconIndex*<br/>
Indeks ikony.

*pShellLink*<br/>
Łącze powłoki, które reprezentuje zadanie ma zostać dodana.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Wystąpienie `CJumpList` gromadzi konkretnych zadań i dodaje je do listy docelowej podczas `CommitList`. Elementy zadań będą wyświetlane w kategorii w dolnej części menu docelowej aplikacji. Ta kategoria mają pierwszeństwo przed wszystkie inne kategorie po wypełnieniu interfejsu użytkownika.

##  <a name="addtasks"></a>  CJumpList::AddTasks

Dodaje elementy do canonical kategorii zadań.

```
BOOL AddTasks(IObjectArray* pObjectCollection);
```

### <a name="parameters"></a>Parametry

*pObjectCollection*<br/>
Kolekcja zadań, które mają zostać dodane.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Wystąpienie CJumpList gromadzi konkretnych zadań i dodaje je do listy docelowej podczas `CommitList`. Elementy zadań będą wyświetlane w kategorii w dolnej części menu docelowej aplikacji. Ta kategoria mają pierwszeństwo przed wszystkie inne kategorie po wypełnieniu interfejsu użytkownika.

##  <a name="addtaskseparator"></a>  CJumpList::AddTaskSeparator

Dodaje separator między zadaniami.

```
BOOL AddTaskSeparator();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli operacja się powiedzie, 0, jeśli nie jest.

##  <a name="cjumplist"></a>  CJumpList::CJumpList

Konstruuje `CJumpList` obiektu.

```
CJumpList(BOOL bAutoCommit = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoCommit*<br/>
Jeśli ten parametr ma wartość FALSE listy nie jest automatycznie zatwierdzone w destruktorze.

##  <a name="clearall"></a>  CJumpList::ClearAll

Usuwa wszystkie zadania i miejsc docelowych, które zostały dodane do bieżącego wystąpienia `CJumpList` do tej pory.

```
void ClearAll();
```

### <a name="remarks"></a>Uwagi

Ta metoda usuwa i zwalnia wszystkie dane i interfejsów wewnętrznych.

##  <a name="clearalldestinations"></a>  CJumpList::ClearAllDestinations

Usuwa wszystkich miejsc docelowych, które zostały dodane do bieżącego wystąpienia CJumpList do tej pory.

```
void ClearAllDestinations();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, jeśli konieczne jest usunięcie wszystkich miejsc docelowych, które zostały dodane do tej pory w bieżącej sesji tworzenia listy docelowej i ponownie dodać innych miejsc docelowych. Jeśli wewnętrzny `ICustomDestinationList` został zainicjowany, zostanie pozostawiony podtrzymywania połączenia.

##  <a name="commitlist"></a>  CJumpList::CommitList

Kończy transakcji tworzenia listy i zatwierdzeń lista zgłoszonych do skojarzonego magazynu (rejestr w tym przypadku).

```
BOOL CommitList();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Zatwierdzenie jest atomic. Jeśli zatwierdzenie zakończy się niepowodzeniem, zostanie zwrócony błąd.  Gdy `CommitList` nosi bieżącej listy elementów usuniętych zostaną wyczyszczone. Wywołanie tej metody resetuje obiekt, tak aby nie ma aktywnych transakcji tworzenia listy. Aby zaktualizować listę, `BeginList` musi być wywoływany ponownie.

##  <a name="getdestinationlist"></a>  CJumpList::GetDestinationList

Pobiera wskaźnik interfejsu do listy docelowej.

```
ICustomDestinationList* GetDestinationList();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Jeśli listy szybkiego dostępu nie został zainicjowany, lub została przekazana lub zostało przerwane, zwrócona wartość będzie równa NULL.

##  <a name="getmaxslots"></a>  CJumpList::GetMaxSlots

Pobiera maksymalną liczbę elementów, w tym nagłówki kategorii, które można wyświetlić w menu docelowej aplikacji wywołującej.

```
UINT GetMaxSlots() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Aplikacje mogą zgłaszać tylko liczbę elementów nagłówki kategorii połączone do tej wartości. Jeśli wywołania `AppendCategory`, `AppendKnownCategory`, lub `AddUserTasks` przekracza tę liczbę, zwracają one błąd.

##  <a name="getremoveditems"></a>  CJumpList::GetRemovedItems

Zwraca tablicę elementów, które reprezentują usunięte miejsc docelowych.

```
IObjectArray* GetRemovedItems();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Usunięto miejsca docelowe są pobierane podczas inicjowania listy szybkiego dostępu. Podczas generowania nowej listy docelowej, aplikacje powinny najpierw przetwarzania listy usunięto miejsc docelowych, czyszcząc dane śledzenia dla każdego elementu zwrócony przez moduł wyliczający listę usuniętych. Jeśli aplikacja próbuje zapewniają elementu, który właśnie został usunięty w transakcji, które bieżące wywołanie `BeginList` pracę, wywołanie metody, która ponownie dodać tego elementu zakończy się niepowodzeniem, aby upewnić się, że aplikacje są troską usunięto listy.

##  <a name="initializelist"></a>  CJumpList::InitializeList

Rozpoczyna się transakcja tworzenia listy.

```
BOOL InitializeList();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Nie trzeba jawnie wywołać tę metodę, jeśli nie chcesz pobrać wskaźnika do `ICustomDestinationList` przy użyciu `GetDestinationList`, liczbę dostępnych gniazd przy użyciu `GetMaxSlots`, lub Podaj listę usuniętych elementów za pomocą `GetRemovedItems`.

##  <a name="setappid"></a>  CJumpList::SetAppID

Określa identyfikator modelu użytkownika aplikacji dla listy, który zostanie skompilowany.

```
void SetAppID(LPCTSTR strAppID);
```

### <a name="parameters"></a>Parametry

*strAppID*<br/>
Ciąg, który określa identyfikator modelu użytkownika aplikacji.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)
