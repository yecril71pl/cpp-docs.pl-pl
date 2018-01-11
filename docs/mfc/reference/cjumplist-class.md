---
title: Klasa CJumpList | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 11b28199155c0ac3bd90cda8fb830ea6f8894dde
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cjumplist-class"></a>Klasa CJumpList
A `CJumpList` znajduje się lista skrótów ujawniony po kliknięciu prawym przyciskiem myszy ikonę na pasku zadań.  
  
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
|[CJumpList::AbortList](#abortlist)|Porzuca transakcję budowania listy bez zatwierdzania.|  
|[CJumpList::AddDestination](#adddestination)|Przeciążone. Dodaje miejsce docelowe do listy.|  
|[CJumpList::AddKnownCategory](#addknowncategory)|Dołącza znane kategorię do listy.|  
|[CJumpList::AddTask](#addtask)|Przeciążone. Dodaje elementy do kategorii zadań kanonicznej.|  
|[CJumpList::AddTasks](#addtasks)|Dodaje elementy do kategorii zadań kanonicznej.|  
|[CJumpList::AddTaskSeparator](#addtaskseparator)|Dodaje separatora między zadaniami.|  
|[CJumpList::ClearAll](#clearall)|Usuwa wszystkie zadania i miejsc docelowych, które zostały dodane do bieżącego wystąpienia elementu `CJumpList` wykonanej do tej pory.|  
|[CJumpList::ClearAllDestinations](#clearalldestinations)|Usuwa wszystkie miejsca docelowe, które zostały dodane do bieżącego wystąpienia elementu `CJumpList` wykonanej do tej pory.|  
|[CJumpList::CommitList](#commitlist)|Kończy się transakcji budowania listy i zatwierdza listy zgłoszone w magazynie skojarzony (rejestr w tym przypadku.)|  
|[CJumpList::GetDestinationList](#getdestinationlist)|Pobiera wskaźnika interfejsu do listy docelowej.|  
|[CJumpList::GetMaxSlots](#getmaxslots)|Pobiera maksymalną liczbę elementów, w tym nagłówków kategorii, które można wyświetlić w aplikacji wywołującej docelowego menu.|  
|[CJumpList::GetRemovedItems](#getremoveditems)|Zwraca tablicę elementów, które reprezentują usunięte miejsc docelowych.|  
|[CJumpList::InitializeList](#initializelist)|Rozpoczyna transakcją tworzenia listy.|  
|[CJumpList::SetAppID](#setappid)|Określa identyfikator modelu użytkownika aplikacji do listy, który zostanie skompilowany.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CJumpList](../../mfc/reference/cjumplist-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxadv.h  
  
##  <a name="_dtorcjumplist"></a>CJumpList:: ~ CJumpList  
 Niszczy `CJumpList` obiektu.  
  
```  
~CJumpList();
```  
  
##  <a name="abortlist"></a>CJumpList::AbortList  
 Porzuca transakcję budowania listy bez zatwierdzania.  
  
```  
void AbortList();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody ma ten sam efekt co niszczenie `CJumpList` bez wywoływania elementu `CommitList`.  
  
##  <a name="adddestination"></a>CJumpList::AddDestination  
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
 `lpcszCategoryName`  
 Określa nazwę kategorii. Określona kategoria nie istnieje, zostanie utworzona.  
  
 `strDestinationPath`  
 Określa ścieżkę do pliku docelowego.  
  
 `strCategoryName`  
 Określa nazwę kategorii. Określona kategoria nie istnieje, zostanie utworzona.  
  
 `pShellItem`  
 Określa element powłoki reprezentujący docelowego dodawany.  
  
 `pShellLink`  
 Określa łącze powłoki reprezentujący docelowego dodawany.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Wystąpienie `CJumpList` wewnętrznie akumuluje dodano miejsc docelowych, a następnie zapisuje je w `CommitList`.  
  
##  <a name="addknowncategory"></a>CJumpList::AddKnownCategory  
 Dołącza znane kategorię do listy.  
  
```  
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```  
  
### <a name="parameters"></a>Parametry  
 `category`  
 Określa typ znanej kategorii. Może to być albo `KDC_RECENT`, lub `KDC_KNOWN`.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Znane są kategorie częste i ostatnie kategorie, które firma Microsoft automatycznie oblicza dla każdej aplikacji, która korzysta z `SHAddToRecentDocs` (lub pośrednio używa jako powłoki wywoła go w imieniu aplikacji w niektórych scenariuszach).  
  
##  <a name="addtask"></a>CJumpList::AddTask  
 Dodaje elementy do kategorii zadań kanonicznej.  
  
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
 `strTargetExecutablePath`  
 Określa ścieżkę docelową zadań.  
  
 `strCommandLineArgs`  
 Określa argumenty wiersza polecenia plik wykonywalny określony przez strTargetExecutablePath.  
  
 `strTitle`  
 Nazwa zadania, który będzie wyświetlany na liście docelowej.  
  
 `strIconLocation`  
 Lokalizacja ikonę, która będzie wyświetlana na liście docelowej, wraz z tytułu.  
  
 `iIconIndex`  
 Indeks ikony.  
  
 `pShellLink`  
 Łącze powłoki reprezentujący zadanie ma zostać dodana.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Wystąpienie `CJumpList` akumuluje określonego zadania i dodaje je do listy docelowej podczas `CommitList`. Elementy zadań będą wyświetlane w kategorii u dołu menu docelowej aplikacji. Ta kategoria ma pierwszeństwo przed wszystkich innych kategoriach po wypełnieniu interfejsu użytkownika.  
  
##  <a name="addtasks"></a>CJumpList::AddTasks  
 Dodaje elementy do kategorii zadań kanonicznej.  
  
```  
BOOL AddTasks(IObjectArray* pObjectCollection);
```  
  
### <a name="parameters"></a>Parametry  
 `pObjectCollection`  
 Kolekcja zadań ma zostać dodana.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Wystąpienie CJumpList akumuluje określonego zadania i dodaje je do listy docelowej podczas `CommitList`. Elementy zadań będą wyświetlane w kategorii u dołu menu docelowej aplikacji. Ta kategoria ma pierwszeństwo przed wszystkich innych kategoriach po wypełnieniu interfejsu użytkownika.  
  
##  <a name="addtaskseparator"></a>CJumpList::AddTaskSeparator  
 Dodaje separatora między zadaniami.  
  
```  
BOOL AddTaskSeparator();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli to się powiedzie, 0, jeśli nie jest.  
  
##  <a name="cjumplist"></a>CJumpList::CJumpList  
 Konstruuje `CJumpList` obiektu.  
  
```  
CJumpList(BOOL bAutoCommit = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bAutoCommit`  
 Jeśli ten parametr ma wartość FALSE listy nie jest automatycznie zadeklarowana w destruktora.  
  
##  <a name="clearall"></a>CJumpList::ClearAll  
 Usuwa wszystkie zadania i miejsc docelowych, które zostały dodane do bieżącego wystąpienia elementu `CJumpList` wykonanej do tej pory.  
  
```  
void ClearAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda usuwa i zwalnia wszystkie dane i wewnętrznych interfejsów.  
  
##  <a name="clearalldestinations"></a>CJumpList::ClearAllDestinations  
 Usuwa wszystkie miejsca docelowe, które zostały dodane do bieżącego wystąpienia CJumpList wykonanej do tej pory.  
  
```  
void ClearAllDestinations();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, jeśli musisz usunąć wszystkie miejsca docelowe, które zostały dodane do tej pory w bieżącej sesji konstruowania listy docelowej, a następnie ponownie Dodaj innych miejsc docelowych. Jeśli wewnętrznej `ICustomDestinationList` został zainicjowany, jest pozostawiany bez aktywności.  
  
##  <a name="commitlist"></a>CJumpList::CommitList  
 Kończy transakcji budowania listy i zatwierdza listy zgłoszone w magazynie skojarzony (rejestr w tym przypadku).  
  
```  
BOOL CommitList();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Zatwierdzanie jest atomic. Jeśli zatwierdzanie nie powiedzie się, zostanie zwrócony błąd.  Gdy `CommitList` jest nazywany bieżącej listy elementów usuniętych zostaną wyczyszczone. Wywołanie tej metody resetuje obiektu, tak aby nie ma aktywnych transakcji tworzenia listy. Aby zaktualizować listę, `BeginList` musi być wywoływany ponownie.  
  
##  <a name="getdestinationlist"></a>CJumpList::GetDestinationList  
 Pobiera wskaźnika interfejsu do listy docelowej.  
  
```  
ICustomDestinationList* GetDestinationList();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Jeśli na liście szybkiego dostępu nie został zainicjowany, lub została przekazana lub przerwane, zostanie zwrócona wartość `NULL`.  
  
##  <a name="getmaxslots"></a>CJumpList::GetMaxSlots  
 Pobiera maksymalną liczbę elementów, w tym nagłówków kategorii, które można wyświetlić w aplikacji wywołującej docelowego menu.  
  
```  
UINT GetMaxSlots() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Aplikacje może zgłaszać tylko liczbę elementów nagłówków kategorii łączyć do tej wartości. Jeśli wywołań `AppendCategory`, `AppendKnownCategory`, lub `AddUserTasks` przekroczeniu tej liczby, ich zwróci błąd.  
  
##  <a name="getremoveditems"></a>CJumpList::GetRemovedItems  
 Zwraca tablicę elementów, które reprezentują usunięte miejsc docelowych.  
  
```  
IObjectArray* GetRemovedItems();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Usunięto miejsca docelowe są pobierane podczas inicjowania listy przeskoku. Podczas generowania nowej listy docelowej, aplikacje powinny najpierw przetworzyć listę usuniętych miejsc docelowych, czyszczenie ich danych śledzenia elementu zwrócony przez moduł wyliczający usuniętych listy. Jeśli aplikacja próbuje udostępnić elementu, który właśnie został usunięty w transakcji, która bieżące wywołanie `BeginList` pracę, wywołanie metody, która ponownie dodać tego elementu zakończy się niepowodzeniem, aby upewnić się, że aplikacje są przestrzeganie usuniętych listy.  
  
##  <a name="initializelist"></a>CJumpList::InitializeList  
 Rozpoczyna transakcją tworzenia listy.  
  
```  
BOOL InitializeList();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Nie trzeba jawnie wywołać tę metodę, jeśli nie chcesz pobrać wskaźnika do `ICustomDestinationList` przy użyciu `GetDestinationList`, liczba dostępnych gniazd przy użyciu `GetMaxSlots`, lub listę usuniętych elementów za pomocą `GetRemovedItems`.  
  
##  <a name="setappid"></a>CJumpList::SetAppID  
 Określa identyfikator modelu użytkownika aplikacji do listy, który zostanie skompilowany.  
  
```  
void SetAppID(LPCTSTR strAppID);
```  
  
### <a name="parameters"></a>Parametry  
 `strAppID`  
 Ciąg określający identyfikator modelu użytkownika aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
