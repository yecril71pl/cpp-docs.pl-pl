---
title: Klasa CRegKey | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CRegKey
- ATLBASE/ATL::CRegKey
- ATLBASE/ATL::CRegKey::CRegKey
- ATLBASE/ATL::CRegKey::Attach
- ATLBASE/ATL::CRegKey::Close
- ATLBASE/ATL::CRegKey::Create
- ATLBASE/ATL::CRegKey::DeleteSubKey
- ATLBASE/ATL::CRegKey::DeleteValue
- ATLBASE/ATL::CRegKey::Detach
- ATLBASE/ATL::CRegKey::EnumKey
- ATLBASE/ATL::CRegKey::Flush
- ATLBASE/ATL::CRegKey::GetKeySecurity
- ATLBASE/ATL::CRegKey::NotifyChangeKeyValue
- ATLBASE/ATL::CRegKey::Open
- ATLBASE/ATL::CRegKey::QueryBinaryValue
- ATLBASE/ATL::CRegKey::QueryDWORDValue
- ATLBASE/ATL::CRegKey::QueryGUIDValue
- ATLBASE/ATL::CRegKey::QueryMultiStringValue
- ATLBASE/ATL::CRegKey::QueryQWORDValue
- ATLBASE/ATL::CRegKey::QueryStringValue
- ATLBASE/ATL::CRegKey::QueryValue
- ATLBASE/ATL::CRegKey::RecurseDeleteKey
- ATLBASE/ATL::CRegKey::SetBinaryValue
- ATLBASE/ATL::CRegKey::SetDWORDValue
- ATLBASE/ATL::CRegKey::SetGUIDValue
- ATLBASE/ATL::CRegKey::SetKeySecurity
- ATLBASE/ATL::CRegKey::SetKeyValue
- ATLBASE/ATL::CRegKey::SetMultiStringValue
- ATLBASE/ATL::CRegKey::SetQWORDValue
- ATLBASE/ATL::CRegKey::SetStringValue
- ATLBASE/ATL::CRegKey::SetValue
- ATLBASE/ATL::CRegKey::m_hKey
- ATLBASE/ATL::CRegKey::m_pTM
dev_langs:
- C++
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6daec3347aecaed3ba0aba5dec106d049a6a701
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cregkey-class"></a>Klasa CRegKey
Ta klasa dostarcza metody do manipulowania wpisy w rejestrze systemu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CRegKey
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRegKey::CRegKey](#cregkey)|Konstruktor.|  
|[CRegKey:: ~ CRegKey](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRegKey::Attach](#attach)|Wywołanie tej metody, aby dołączyć HKEY do `CRegKey` obiektu przez ustawienie [m_hKey](#m_hkey) uchwytu elementu członkowskiego do `hKey`.|  
|[CRegKey::Close](#close)|Wywołanie tej metody, aby zwolnić [m_hKey](#m_hkey) element członkowski obsługi i ustaw ją na wartość NULL.|  
|[CRegKey::Create](#create)|Wywołanie tej metody można utworzyć określony klucz, jeśli nie istnieje jako podklucz `hKeyParent`.|  
|[CRegKey::DeleteSubKey](#deletesubkey)|Wywołaj tę metodę w celu usunięcia określonego klucza z rejestru.|  
|[CRegKey::DeleteValue](#deletevalue)|Wywołanie tej metody, aby usunąć pola wartości z [m_hKey](#m_hkey).|  
|[CRegKey::Detach](#detach)|Wywołanie tej metody można odłączyć [m_hKey](#m_hkey) uchwytu elementu członkowskiego z `CRegKey` obiektu i ustaw `m_hKey` na wartość NULL.|  
|[CRegKey::EnumKey](#enumkey)|Wywołanie tej metody można wyliczyć podkluczy klucza rejestru otwarte.|  
|[CRegKey::Flush](#flush)|Wywołaj tę metodę, aby zapisać wszystkie atrybuty otworzyć klucza rejestru do rejestru.|  
|[CRegKey::GetKeySecurity](#getkeysecurity)|Wywołaj tę metodę, aby pobrać kopię deskryptora zabezpieczeń, ochrony otworzyć klucza rejestru.|  
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|Ta metoda powiadamia wywołującego o zmianach atrybuty lub zawartość otworzyć klucza rejestru.|  
|[CRegKey::Open](#open)|Wywołanie tej metody, aby otworzyć określony klucz i ustawić [m_hKey](#m_hkey) do realizacji tego klucza.|  
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|Wywołanie tej metody do pobierania danych binarnych dla nazwy określonej wartości.|  
|[CRegKey::QueryDWORDValue](#querydwordvalue)|Wywołaj tę metodę, aby pobrać dane DWORD o nazwę określonej wartości.|  
|[CRegKey::QueryGUIDValue](#queryguidvalue)|Wywołanie tej metody do pobierania danych identyfikatora GUID dla nazwy określonej wartości.|  
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|Wywołaj tę metodę w celu pobrania danych wielociągu dla nazwy określonej wartości.|  
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|Wywołanie tej metody do pobierania danych QWORD dla nazwy określonej wartości.|  
|[CRegKey::QueryStringValue](#querystringvalue)|Wywołanie tej metody do pobierania danych ciągu dla nazwy określonej wartości.|  
|[CRegKey::QueryValue](#queryvalue)|Wywołanie tej metody do pobierania danych dla określonej wartości pola [m_hKey](#m_hkey). Starsze wersje tej metody nie są już obsługiwane i są oznaczone jako **ATL_DEPRECATED**.|  
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|Wywołaj tę metodę w celu usunięcia określonego klucza z rejestru i usunąć wszystkie podklucze.|  
|[CRegKey::SetBinaryValue](#setbinaryvalue)|Wywołanie tej metody można ustawić wartości binarnej klucza rejestru.|  
|[CRegKey::SetDWORDValue](#setdwordvalue)|Wywołanie tej metody można ustawić wartości DWORD klucza rejestru.|  
|[CRegKey::SetGUIDValue](#setguidvalue)|Wywołaj tę metodę, aby ustawić wartość identyfikatora GUID klucza rejestru.|  
|[CRegKey::SetKeySecurity](#setkeysecurity)|Wywołanie tej metody można ustawić zabezpieczeń klucza rejestru.|  
|[CRegKey::SetKeyValue](#setkeyvalue)|Wywołanie tej metody do przechowywania danych w polu określoną wartość z określonym kluczem.|  
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|Wywołanie tej metody, aby ustawić wartość wielociągu klucza rejestru.|  
|[CRegKey::SetQWORDValue](#setqwordvalue)|Wywołaj tę metodę, aby ustawić wartość QWORD klucza rejestru.|  
|[CRegKey::SetStringValue](#setstringvalue)|Wywołaj tę metodę, aby ustawić wartość ciągu klucza rejestru.|  
|[CRegKey::SetValue](#setvalue)|Wywołanie tej metody do przechowywania danych w polu określonej wartości [m_hKey](#m_hkey). Starsze wersje tej metody nie są już obsługiwane i są oznaczone jako **ATL_DEPRECATED**.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRegKey::operator HKEY](#operator_hkey)|Konwertuje `CRegKey` obiektu HKEY.|  
|[CRegKey::operator =](#operator_eq)|Operator przypisania.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRegKey::m_hKey](#m_hkey)|Zawiera dojście do klucza rejestru, skojarzone z `CRegKey` obiektu.|  
|[CRegKey::m_pTM](#m_ptm)|Wskaźnik do `CAtlTransactionManager` obiektu|  
  
## <a name="remarks"></a>Uwagi  
 `CRegKey` udostępnia metody do tworzenia i usuwania kluczy i wartości w rejestrze systemu. Rejestr zawiera specyficznych dla instalacji zestawu definicji dla składników systemu, takich jak numery wersji oprogramowania, mapowania logiczne fizyczne zainstalowanego sprzętu i obiektów COM.  
  
 `CRegKey` udostępnia interfejs programowania do rejestru systemowego dla danej maszyny. Na przykład można otworzyć klucza rejestru w szczególności, należy wywołać `CRegKey::Open`. Aby pobrać lub zmodyfikować wartość danych, należy wywołać `CRegKey::QueryValue` lub `CRegKey::SetValue`odpowiednio. Aby zamknąć klucza, należy wywołać `CRegKey::Close`.  
  
 Po zamknięciu klucza, jego dane rejestru są zapisywane (wyczyszczone) na dysku twardym. Ten proces może potrwać kilka sekund. Jeśli aplikacja musi jawnie zapisać danych rejestru dysku twardego, należy wywołać [RegFlushKey](http://msdn.microsoft.com/library/windows/desktop/ms724867) funkcji Win32. Jednak **RegFlushKey** używa wielu zasobów systemowych i powinna być wywoływana tylko wtedy, gdy jest to bezwzględnie konieczne.  
  
> [!IMPORTANT]
>  Żadnych metod umożliwiających obiekt wywołujący, aby określić lokalizację rejestru mieć możliwość odczytu danych, która nie może być zaufane. Użycie metody, które należy [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) należy wziąć pod uwagę, że ta funkcja nie obsługuje jawnie ciągów, które są zakończone znakiem NULL. Oba te warunki mają być wyszukiwane przez kod wywołujący.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="attach"></a>  CRegKey::Attach  
 Wywołanie tej metody, aby dołączyć HKEY do `CRegKey` obiektu przez ustawienie [m_hKey](#m_hkey) uchwytu elementu członkowskiego do `hKey`.  
  
```
void Attach(HKEY hKey) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hKey`  
 Dojście do klucza rejestru.  
  
### <a name="remarks"></a>Uwagi  
 **Dołącz** będzie assert, jeśli `m_hKey` jest różna od NULL.  
  
##  <a name="close"></a>  CRegKey::Close  
 Wywołanie tej metody, aby zwolnić [m_hKey](#m_hkey) element członkowski obsługi i ustaw ją na wartość NULL.  
  
```
LONG Close() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie zwraca wartość błędu.  
  
##  <a name="create"></a>  CRegKey::Create  
 Wywołanie tej metody można utworzyć określony klucz, jeśli nie istnieje jako podklucz `hKeyParent`.  
  
```
LONG Create(  
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPTSTR lpszClass = REG_NONE,
    DWORD dwOptions = REG_OPTION_NON_VOLATILE,
    REGSAM samDesired = KEY_READ | KEY_WRITE,
    LPSECURITY_ATTRIBUTES lpSecAttr = NULL,
    LPDWORD lpdwDisposition = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hKeyParent`  
 Dojście otwartego klucza.  
  
 `lpszKeyName`  
 Określa nazwę klucza do utworzenia lub otwarcia. Ta nazwa musi być podklucz `hKeyParent`.  
  
 `lpszClass`  
 Określa klasę klucza do utworzenia lub otwarcia. Wartość domyślna to REG_NONE.  
  
 `dwOptions`  
 Opcje dla klucza. Wartość domyślna to REG_OPTION_NON_VOLATILE. Aby uzyskać listę możliwych wartości i opisy, zobacz [RegCreateKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724844) w zestawie Windows SDK.  
  
 `samDesired`  
 Zabezpieczeń dostępu do klucza. Wartość domyślna to KEY_READ &#124; KEY_WRITE. Aby uzyskać listę możliwych wartości i opisy, zobacz **RegCreateKeyEx**.  
  
 *lpSecAttr*  
 Wskaźnik do [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) struktury, która wskazuje, czy dojście klucza mogą być dziedziczone przez procesu podrzędnego. Domyślnie ten parametr ma wartość NULL (znaczenie, które nie może być dziedziczona dojście).  
  
 *lpdwDisposition*  
 [out] Jeśli inną niż NULL, pobiera REG_CREATED_NEW_KEY (Jeśli klucz nie istnieje i został utworzony) lub REG_OPENED_EXISTING_KEY (Jeśli klucz istniał i został otwarty).  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca ERROR_SUCCESS i otwiera klucza. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowane w powiodło się. kod błędu różną od zera. H.  
  
### <a name="remarks"></a>Uwagi  
 **Utwórz** ustawia [m_hKey](#m_hkey) elementu członkowskiego do realizacji tego klucza.  
  
##  <a name="cregkey"></a>  CRegKey::CRegKey  
 Konstruktor.  
  
```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Odwołanie do `CRegKey` obiektu.  
  
 `hKey`  
 Dojście do klucza rejestru.  
  
 `pTM`  
 Wskaźnik do obiektu CAtlTransactionManager  
  
### <a name="remarks"></a>Uwagi  
 Tworzy nową `CRegKey` obiektu. Można utworzyć obiektu z istniejącego `CRegKey` obiektu lub dojście do klucza rejestru.  
  
##  <a name="dtor"></a>  CRegKey:: ~ CRegKey  
 Destruktor.  
  
```
~CRegKey() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Wersje destruktora `m_hKey`.  
  
##  <a name="deletesubkey"></a>  CRegKey::DeleteSubKey  
 Wywołaj tę metodę w celu usunięcia określonego klucza z rejestru.  
  
```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszSubKey`  
 Określa nazwę klucza do usunięcia. Ta nazwa musi być podklucz [m_hKey](#m_hkey).  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowane w powiodło się. kod błędu różną od zera. H.  
  
### <a name="remarks"></a>Uwagi  
 `DeleteSubKey` można usunąć tylko klucz, który ma podklucze nie. Jeśli klucz ma podklucze, wywołanie [RecurseDeleteKey](#recursedeletekey) zamiast tego.  
  
##  <a name="deletevalue"></a>  CRegKey::DeleteValue  
 Wywołanie tej metody, aby usunąć pola wartości z [m_hKey](#m_hkey).  
  
```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszValue`  
 Określa pole wartości do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowane w powiodło się. kod błędu różną od zera. H.  
  
##  <a name="detach"></a>  CRegKey::Detach  
 Wywołanie tej metody można odłączyć [m_hKey](#m_hkey) uchwytu elementu członkowskiego z `CRegKey` obiektu i ustaw `m_hKey` na wartość NULL.  
  
```
HKEY Detach() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Klucz HKEY skojarzone z `CRegKey` obiektu.  
  
##  <a name="enumkey"></a>  CRegKey::EnumKey  
 Wywołanie tej metody można wyliczyć podkluczy klucza rejestru otwarte.  
  
```
LONG EnumKey(  
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `iIndex`  
 Indeks podkluczy. Ten parametr powinien być zero jako pierwsze wywołanie i zwiększana w kolejnych wywołaniach  
  
 `pszName`  
 Wskaźnik do buforu, który odbiera nazwa podklucza, w tym znak końcowy null. Nazwa podklucza jest kopiowana do buforu, nie hierarchii pełnej klucza.  
  
 *pnNameLength*  
 Wskaźnik do zmiennej, która określa rozmiar w TCHARs buforu określony przez `pszName` parametru. Ten rozmiar powinna zawierać znak końcowy null. Gdy metoda zwróci wartość, wskazywanej przez zmienną *pnNameLength* zawiera liczbę znaków przechowywanych w buforze. Liczba zwrócił nie zawiera znak końcowy null.  
  
 *pftLastWriteTime*  
 Wskaźnik do zmiennej, która odbiera czas ostatniego zapisania podklucz wyliczany do.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowane w powiodło się. kod błędu różną od zera. H.  
  
### <a name="remarks"></a>Uwagi  
 Aby wyliczyć podkluczy, należy wywołać `CRegKey::EnumKey` o indeksie zero. Zwiększ wartość indeksu i powtórz metoda zwraca ERROR_NO_MORE_ITEMS. Aby uzyskać więcej informacji, zobacz [RegEnumKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724862) w zestawie Windows SDK.  
  
##  <a name="flush"></a>  CRegKey::Flush  
 Wywołaj tę metodę, aby zapisać wszystkie atrybuty otworzyć klucza rejestru do rejestru.  
  
```
LONG Flush() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowane w powiodło się. kod błędu różną od zera. H.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [RegEnumFlush](http://msdn.microsoft.com/library/windows/desktop/ms724867) w zestawie Windows SDK.  
  
##  <a name="getkeysecurity"></a>  CRegKey::GetKeySecurity  
 Wywołaj tę metodę, aby pobrać kopię deskryptora zabezpieczeń, ochrony otworzyć klucza rejestru.  
  
```
LONG GetKeySecurity(  
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `si`  
 [SECURITY_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/aa379573) wartość, która wskazuje żądane informacje o zabezpieczeniach.  
  
 `psd`  
 Wskaźnik do buforu, który otrzyma kopię deskryptora zabezpieczeń żądanej.  
  
 `pnBytes`  
 Rozmiar w bajtach buforu wskazywana przez `psd`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest niezerowa błąd jest zdefiniowany w powiodło się. H.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [RegGetKeySecurity](http://msdn.microsoft.com/library/windows/desktop/aa379313).  
  
##  <a name="m_hkey"></a>  CRegKey::m_hKey  
 Zawiera dojście do klucza rejestru, skojarzone z `CRegKey` obiektu.  
  
```
HKEY m_hKey;
```  
  
##  <a name="m_ptm"></a>  CRegKey::m_pTM  
 Wskaźnik do `CAtlTransactionManager` obiektu.  
  
```
CAtlTransactionManager* m_pTM;
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="notifychangekeyvalue"></a>  CRegKey::NotifyChangeKeyValue  
 Ta metoda powiadamia wywołującego o zmianach atrybuty lub zawartość otworzyć klucza rejestru.  
  
```
LONG NotifyChangeKeyValue(  
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *bWatchSubtree*  
 Określa flagę wskazującą, czy zgłaszać zmiany w określonym kluczem i wszystkich jego podkluczy lub tylko określonego klucza. Jeśli ten parametr ma wartość TRUE, metoda zgłasza zmian w kluczu i jego podkluczach. Jeśli parametr ma wartość FALSE, metoda zgłasza zmiany tylko w kluczu.  
  
 *dwNotifyFilter*  
 Określa, że należy podać zestaw flagi sterujące, jakie zmiany. Ten parametr może mieć kombinację następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|REG_NOTIFY_CHANGE_NAME|Powiadomić wywołującego, jeśli podklucz zostanie dodany lub usunięty.|  
|REG_NOTIFY_CHANGE_ATTRIBUTES|Powiadomić wywołującego zmiany atrybutów klucza, takie jak informacje deskryptora zabezpieczeń.|  
|REG_NOTIFY_CHANGE_LAST_SET|Powiadomić wywołującego zmiana wartości klucza. Mogą to być Dodawanie lub usuwanie wartość lub zmianę istniejącej wartości.|  
|REG_NOTIFY_CHANGE_SECURITY|Powiadomić wywołującego zmian do deskryptora zabezpieczeń klucza.|  
  
 `hEvent`  
 Dojście do zdarzenia. Jeśli *bAsync* parametr ma wartość TRUE, metoda zwraca natychmiast i zmiany są zgłaszane przez sygnalizowania tego zdarzenia. Jeśli `bAsync` ma wartość FALSE, `hEvent` jest ignorowana.  
  
 `bAsync`  
 Określa flagi, która wskazuje, jak metoda zgłasza zmiany. Jeśli ten parametr ma wartość TRUE, metoda zwraca natychmiast i raporty zmian przez sygnalizowania określone zdarzenie. Jeśli ten parametr ma wartość FALSE, metoda nie zwraca dopóki nastąpiła zmiana. Jeśli `hEvent` nie został określony prawidłowy zdarzenia `bAsync` parametr nie może mieć wartość TRUE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowane w powiodło się. kod błędu różną od zera. H.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda nie powiadomić wywołującego, jeśli określony klucz jest usuwany.  
  
 Dalsze szczegółowe informacje i przykładowy program, zobacz [wywołanie funkcji RegNotifyChangeKeyValue](http://msdn.microsoft.com/library/windows/desktop/ms724892).  
  
##  <a name="open"></a>  CRegKey::Open  
 Wywołanie tej metody, aby otworzyć określony klucz i ustawić [m_hKey](#m_hkey) do realizacji tego klucza.  
  
```
LONG Open(  
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hKeyParent`  
 Dojście otwartego klucza.  
  
 `lpszKeyName`  
 Określa nazwę klucza do utworzenia lub otwarcia. Ta nazwa musi być podklucz `hKeyParent`.  
  
 `samDesired`  
 Zabezpieczeń dostępu do klucza. Wartość domyślna to KEY_ALL_ACCESS. Aby uzyskać listę możliwych wartości i opisy, zobacz [RegCreateKeyEx](http://msdn.microsoft.com/library/windows/desktop/ms724844) w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie wartość niezerową błąd zdefiniowany w powiodło się. H.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `lpszKeyName` parametr ma wartość NULL lub punktów na pusty ciąg, **Otwórz** otwiera nowy uchwyt klucz identyfikowany przez `hKeyParent`, ale nie zamyka wszystkie wcześniej otwarte dojście.  
  
 W odróżnieniu od [CRegKey::Create](#create), **Otwórz** nie utworzy określony klucz, jeśli nie istnieje.  
  
##  <a name="operator_hkey"></a>  CRegKey::operator HKEY  
 Konwertuje `CRegKey` obiektu HKEY.  
  
```  
operator HKEY() const throw();
```  
  
##  <a name="operator_eq"></a>  CRegKey::operator =  
 Operator przypisania.  
  
```
CRegKey& operator= (CRegKey& key) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do nowego klucza.  
  
### <a name="remarks"></a>Uwagi  
 Odłącza tego operatora `key` z jego bieżący obiekt, a następnie przypisuje go do `CRegKey` zamiast tego obiektu.  
  
##  <a name="querybinaryvalue"></a>  CRegKey::QueryBinaryValue  
 Wywołanie tej metody do pobierania danych binarnych dla nazwy określonej wartości.  
  
```
LONG QueryBinaryValue(  
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Wskaźnik do zerem ciąg zawierający nazwę wartości do zapytania.  
  
 `pValue`  
 Wskaźnik do buforu, który odbiera dane tej wartości.  
  
 `pnBytes`  
 Wskaźnik do zmiennej, która określa rozmiar w bajtach buforu wskazywana przez `pValue` parametru. Gdy metoda zwróci wartość, ta zmienna uwzględnia rozmiar danych kopiowania do buforu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwracany jest ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca zdefiniowane w powiodło się. kod błędu różną od zera. H. Jeśli odwołuje się do danych nie jest typu REG_BINARY, zwracany jest ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda korzysta z **RegQueryValueEx** i potwierdza, że zwracana jest poprawny typ danych. Zobacz [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) więcej szczegółów.  
  
> [!IMPORTANT]
>  Ta metoda umożliwia obiekt wywołujący, aby określić dowolną lokalizację rejestru, potencjalny Odczyt danych, która nie jest zaufany. Ponadto [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) funkcja używane przez tę metodę nie obsługuje jawnie ciągów, które są zakończone znakiem NULL. Oba te warunki mają być wyszukiwane przez kod wywołujący.  
  
##  <a name="querydwordvalue"></a>  CRegKey::QueryDWORDValue  
 Wywołaj tę metodę, aby pobrać dane DWORD o nazwę określonej wartości.  
  
```
LONG QueryDWORDValue(  
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Wskaźnik do zerem ciąg zawierający nazwę wartości do zapytania.  
  
 `dwValue`  
 Wskaźnik do buforu, który odbiera wartość typu DWORD.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwracany jest ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca zdefiniowane w powiodło się. kod błędu różną od zera. H. Jeśli odwołuje się do danych nie jest typu REG_DWORD, zwracany jest ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda korzysta z **RegQueryValueEx** i potwierdza, że zwracana jest poprawny typ danych. Zobacz [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) więcej szczegółów.  
  
> [!IMPORTANT]
>  Ta metoda umożliwia obiekt wywołujący, aby określić dowolną lokalizację rejestru, potencjalny Odczyt danych, która nie jest zaufany. Ponadto [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) funkcja używane przez tę metodę nie obsługuje jawnie ciągów, które są zakończone znakiem NULL. Oba te warunki mają być wyszukiwane przez kod wywołujący.  
  
##  <a name="queryguidvalue"></a>  CRegKey::QueryGUIDValue  
 Wywołanie tej metody do pobierania danych identyfikatora GUID dla nazwy określonej wartości.  
  
```
LONG QueryGUIDValue(  
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Wskaźnik do zerem ciąg zawierający nazwę wartości do zapytania.  
  
 `guidValue`  
 Wskaźnik do zmiennej, która odbiera identyfikatora GUID.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwracany jest ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca zdefiniowane w powiodło się. kod błędu różną od zera. H. Jeśli odwołuje się do danych nie jest prawidłowym identyfikatorem GUID, zwracany jest ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda korzysta z `CRegKey::QueryStringValue` i konwertuje ciąg na identyfikator GUID za pomocą [CLSIDFromString](http://msdn.microsoft.com/library/windows/desktop/ms680589).  
  
> [!IMPORTANT]
>  Ta metoda umożliwia obiekt wywołujący, aby określić dowolną lokalizację rejestru, potencjalny Odczyt danych, która nie jest zaufany.  
  
##  <a name="querymultistringvalue"></a>  CRegKey::QueryMultiStringValue  
 Wywołaj tę metodę w celu pobrania danych wielociągu dla nazwy określonej wartości.  
  
```
LONG QueryMultiStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Wskaźnik do zerem ciąg zawierający nazwę wartości do zapytania.  
  
 `pszValue`  
 Wskaźnik do buforu, który odbiera dane wielociągu. Kolumny jest tablicą ciągów zerem został przerwany przez dwa znaki null.  
  
 `pnChars`  
 Rozmiar w TCHARs buforu wskazywana przez `pszValue`. Gdy metoda zwróci wartość, `pnChars` zawiera rozmiar w TCHARs z kolumny pobrać, w tym znak końcowy null.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwracany jest ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca zdefiniowane w powiodło się. kod błędu różną od zera. H. Jeśli odwołuje się do danych nie jest typu REG_MULTI_SZ, zwracany jest ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda korzysta z **RegQueryValueEx** i potwierdza, że zwracana jest poprawny typ danych. Zobacz [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) więcej szczegółów.  
  
> [!IMPORTANT]
>  Ta metoda umożliwia obiekt wywołujący, aby określić dowolną lokalizację rejestru, potencjalny Odczyt danych, która nie jest zaufany. Ponadto [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) funkcja używane przez tę metodę nie obsługuje jawnie ciągów, które są zakończone znakiem NULL. Oba te warunki mają być wyszukiwane przez kod wywołujący.  
  
##  <a name="queryqwordvalue"></a>  CRegKey::QueryQWORDValue  
 Wywołanie tej metody do pobierania danych QWORD dla nazwy określonej wartości.  
  
```
LONG QueryQWORDValue(  
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Wskaźnik do zerem ciąg zawierający nazwę wartości do zapytania.  
  
 `qwValue`  
 Wskaźnik do buforu, który odbiera QWORD.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwracany jest ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca zdefiniowane w powiodło się. kod błędu różną od zera. H. Jeśli odwołuje się do danych nie jest typu REG_QWORD, zwracany jest ERROR_INVALID_DATA.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda korzysta z **RegQueryValueEx** i potwierdza, że zwracana jest poprawny typ danych. Zobacz [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) więcej szczegółów.  
  
> [!IMPORTANT]
>  Ta metoda umożliwia obiekt wywołujący, aby określić dowolną lokalizację rejestru, potencjalny Odczyt danych, która nie jest zaufany. Ponadto [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) funkcja używane przez tę metodę nie obsługuje jawnie ciągów, które są zakończone znakiem NULL. Oba te warunki mają być wyszukiwane przez kod wywołujący.  
  
##  <a name="querystringvalue"></a>  CRegKey::QueryStringValue  
 Wywołanie tej metody do pobierania danych ciągu dla nazwy określonej wartości.  
  
```
LONG QueryStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Wskaźnik do zerem ciąg zawierający nazwę wartości do zapytania.  
  
 `pszValue`  
 Wskaźnik do buforu, który odbiera dane ciągu.  
  
 `pnChars`  
 Rozmiar w TCHARs buforu wskazywana przez `pszValue`. Gdy metoda zwróci wartość, `pnChars` zawiera rozmiar w TCHARs ciągu pobrać, w tym znak końcowy null.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwracany jest ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca zdefiniowane w powiodło się. kod błędu różną od zera. H. Jeśli odwołuje się do danych nie jest typu REG_SZ, zwracany jest ERROR_INVALID_DATA. Jeśli metoda zwraca kod ERROR_MORE_DATA, `pnChars` równa zero nie wymagany rozmiar buforu w bajtach.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda korzysta z **RegQueryValueEx** i potwierdza, że zwracana jest poprawny typ danych. Zobacz [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) więcej szczegółów.  
  
> [!IMPORTANT]
>  Ta metoda umożliwia obiekt wywołujący, aby określić dowolną lokalizację rejestru, potencjalny Odczyt danych, która nie jest zaufany. Ponadto [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) funkcja używane przez tę metodę nie obsługuje jawnie ciągów, które są zakończone znakiem NULL. Oba te warunki mają być wyszukiwane przez kod wywołujący.  
  
##  <a name="queryvalue"></a>  CRegKey::QueryValue  
 Wywołanie tej metody do pobierania danych dla określonej wartości pola [m_hKey](#m_hkey). Starsze wersje tej metody nie są już obsługiwane i są oznaczone jako **ATL_DEPRECATED**.  
  
```
LONG QueryValue(  
    LPCTSTR pszValueName,
    DWORD* pdwType,
    void* pData,
    ULONG* pnBytes) throw();

ATL_DEPRECATED LONG QueryValue(
    DWORD& dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG QueryValue(
    LPTSTR szValue,
    LPCTSTR lpszValueName,
    DWORD* pdwCount);
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Wskaźnik do zerem ciąg zawierający nazwę wartości do zapytania. Jeśli `pszValueName` ma wartość NULL lub pusty ciąg "" metoda pobiera typ i dane dla klucza bez jego nazwy lub wartość domyślna, jeśli istnieje.  
  
 `pdwType`  
 Wskaźnik do zmiennej, która odbiera kod wskazujący typ danych przechowywanych w określonej wartości. `pdwType` Parametr może mieć wartość NULL, jeśli kod typu nie jest wymagana.  
  
 `pData`  
 Wskaźnik do buforu, który odbiera dane tej wartości. Ten parametr może mieć wartości NULL, jeśli dane nie są wymagane.  
  
 `pnBytes`  
 Wskaźnik do zmiennej, która określa rozmiar w bajtach buforu wskazywana przez `pData` parametru. Gdy metoda zwróci wartość, ta zmienna uwzględnia rozmiar danych skopiowane do *pData.*  
  
 `dwValue`  
 Pole wartości danych numerycznych.  
  
 `lpszValueName`  
 Określa wartość pola można wykonać zapytania.  
  
 `szValue`  
 Pole wartości danych ciągu.  
  
 `pdwCount`  
 Rozmiar danych ciągu. Jego wartość jest początkowo ustawiona rozmiar `szValue` buforu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie wartość niezerową błąd zdefiniowany w powiodło się. H.  
  
### <a name="remarks"></a>Uwagi  
 Dwie wersje oryginalnego `QueryValue` nie są już obsługiwane i są oznaczone jako **ATL_DEPRECATED**. Kompilator będzie ostrzeżenie, jeśli formularze te są używane.  
  
 Pozostałe wywołania metody RegQueryValueEx.  
  
> [!IMPORTANT]
>  Ta metoda umożliwia obiekt wywołujący, aby określić dowolną lokalizację rejestru, potencjalny Odczyt danych, która nie jest zaufany. Ponadto funkcja RegQueryValueEx używane przez tę metodę nie obsługuje jawnie ciągów, które są `NULL` zakończone. Oba te warunki mają być wyszukiwane przez kod wywołujący.  
  
##  <a name="recursedeletekey"></a>  CRegKey::RecurseDeleteKey  
 Wywołaj tę metodę w celu usunięcia określonego klucza z rejestru i usunąć wszystkie podklucze.  
  
```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszKey*  
 Określa nazwę klucza do usunięcia. Ta nazwa musi być podklucz [m_hKey](#m_hkey).  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie wartość niezerową błąd zdefiniowany w powiodło się. H.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli klucz ma podklucze, należy wywołać tę metodę, aby usunąć klucz.  
  
##  <a name="setbinaryvalue"></a>  CRegKey::SetBinaryValue  
 Wywołanie tej metody można ustawić wartości binarnej klucza rejestru.  
  
```
LONG SetBinaryValue(  
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Wskaźnik do ciągu zawierającego nazwę wartość do ustawienia. Jeśli wartość o tej nazwie nie jest już istnieje, metoda dodaje do klucza.  
  
 `pValue`  
 Wskaźnik do buforu, zawierający dane, które mają być przechowywane o nazwie określonej wartości.  
  
 `nBytes`  
 Określa rozmiar w bajtach informacji wskazywana przez `pValue` parametru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowane w powiodło się. kod błędu różną od zera. H.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda używa [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923) do zapisu wartości do rejestru.  
  
##  <a name="setdwordvalue"></a>  CRegKey::SetDWORDValue  
 Wywołanie tej metody można ustawić wartości DWORD klucza rejestru.  
  
```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Wskaźnik do ciągu zawierającego nazwę wartość do ustawienia. Jeśli wartość o tej nazwie nie jest już istnieje, metoda dodaje do klucza.  
  
 `dwValue`  
 DWORD przechowywania danych o nazwie określonej wartości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowane w powiodło się. kod błędu różną od zera. H.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda używa [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923) do zapisu wartości do rejestru.  
  
##  <a name="setguidvalue"></a>  CRegKey::SetGUIDValue  
 Wywołaj tę metodę, aby ustawić wartość identyfikatora GUID klucza rejestru.  
  
```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Wskaźnik do ciągu zawierającego nazwę wartość do ustawienia. Jeśli wartość o tej nazwie nie jest już istnieje, metoda dodaje do klucza.  
  
 `guidValue`  
 Odwołanie do identyfikatora GUID do przechowywania o nazwie określonej wartości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowane w powiodło się. kod błędu różną od zera. H.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda korzysta z `CRegKey::SetStringValue` i konwertuje identyfikator GUID na ciąg za pomocą [StringFromGUID2](http://msdn.microsoft.com/library/windows/desktop/ms683893).  
  
##  <a name="setkeyvalue"></a>  CRegKey::SetKeyValue  
 Wywołanie tej metody do przechowywania danych w polu określoną wartość z określonym kluczem.  
  
```
LONG SetKeyValue(  
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszKeyName`  
 Określa nazwę klucza do utworzenia lub otwarcia. Ta nazwa musi być podklucz [m_hKey](#m_hkey).  
  
 `lpszValue`  
 Określa dane, które mają być przechowywane. Ten parametr musi mieć wartości NULL.  
  
 `lpszValueName`  
 Określa pole wartość do ustawienia. Jeśli wartość pola o tej nazwie nie istnieje już w kluczu, jest dodawany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie wartość niezerową błąd zdefiniowany w powiodło się. H.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody można utworzyć lub otworzyć `lpszKeyName` klucza i przechowywać `lpszValue` danych w `lpszValueName` wartość pola.  
  
##  <a name="setkeysecurity"></a>  CRegKey::SetKeySecurity  
 Wywołanie tej metody można ustawić zabezpieczeń klucza rejestru.  
  
```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `si`  
 Określa składniki można ustawić deskryptora zabezpieczeń. Wartość może być kombinacją następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|DACL_SECURITY_INFORMATION|Ustawia klucz listy DACL kontroli dostępu (DACL). Klucz musi mieć dostęp WRITE_DAC lub proces wywołujący musi być właściciela obiektu.|  
|GROUP_SECURITY_INFORMATION|Ustawia klucz podstawowy grupy-identyfikator zabezpieczeń (SID). Klucz musi mieć dostęp WRITE_OWNER lub proces wywołujący musi być właściciela obiektu.|  
|OWNER_SECURITY_INFORMATION|Ustawia identyfikator SID właściciela klucza. Klucz musi mieć dostęp WRITE_OWNER lub proces wywołujący musi być właściciela obiektu lub mieć włączone uprawnienia SE_TAKE_OWNERSHIP_NAME.|  
|SACL_SECURITY_INFORMATION|Ustawia listę kontroli dostępu systemu klucza (SACL). Klucz musi mieć dostęp ACCESS_SYSTEM_SECURITY. Właściwy sposób, aby uzyskać dostęp, jest umożliwienie SE_SECURITY_NAME [uprawnień](http://msdn.microsoft.com/library/windows/desktop/aa379306) wywołującego bieżącego tokenu dostępu, otworzyć uchwytu ACCESS_SYSTEM_SECURITY dostępu, a następnie wyłącz odpowiednie uprawnienie.|  
  
 `psd`  
 Wskaźnik do [SECURITY_DESCRIPTOR](http://msdn.microsoft.com/library/windows/desktop/aa379561) struktury, która określa atrybuty zabezpieczeń można ustawić dla określonego klucza.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowane w powiodło się. kod błędu różną od zera. H.  
  
### <a name="remarks"></a>Uwagi  
 Ustawia atrybuty zabezpieczeń klucza. Zobacz [RegSetKeySecurity](http://msdn.microsoft.com/library/windows/desktop/aa379314) więcej szczegółów.  
  
##  <a name="setmultistringvalue"></a>  CRegKey::SetMultiStringValue  
 Wywołanie tej metody, aby ustawić wartość wielociągu klucza rejestru.  
  
```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Wskaźnik do ciągu zawierającego nazwę wartość do ustawienia. Jeśli wartość o tej nazwie nie jest już istnieje, metoda dodaje do klucza.  
  
 `pszValue`  
 Wskaźnik do wielociągu dane mają być przechowywane o nazwie określonej wartości. Kolumny jest tablicą ciągów zerem został przerwany przez dwa znaki null.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowane w powiodło się. kod błędu różną od zera. H.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda używa [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923) do zapisu wartości do rejestru.  
  
##  <a name="setqwordvalue"></a>  CRegKey::SetQWORDValue  
 Wywołaj tę metodę, aby ustawić wartość QWORD klucza rejestru.  
  
```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Wskaźnik do ciągu zawierającego nazwę wartość do ustawienia. Jeśli wartość o tej nazwie nie jest już istnieje, metoda dodaje do klucza.  
  
 `qwValue`  
 QWORD przechowywania danych o nazwie określonej wartości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowane w powiodło się. kod błędu różną od zera. H.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda używa [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923) do zapisu wartości do rejestru.  
  
##  <a name="setstringvalue"></a>  CRegKey::SetStringValue  
 Wywołaj tę metodę, aby ustawić wartość ciągu klucza rejestru.  
  
```
LONG SetStringValue(  
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Wskaźnik do ciągu zawierającego nazwę wartość do ustawienia. Jeśli wartość o tej nazwie nie jest już istnieje, metoda dodaje do klucza.  
  
 `pszValue`  
 Wskaźnik do przechowywania o nazwie określonej wartości danych ciągu.  
  
 `dwType`  
 Typ parametrów do zapisu w rejestrze: REG_SZ (ustawienie domyślne) lub REG_EXPAND_SZ (dla multistrings).  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowane w powiodło się. kod błędu różną od zera. H.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda używa [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923\(v=vs.85\).aspx) do zapisu wartości do rejestru.  
  
##  <a name="setvalue"></a>  CRegKey::SetValue  
 Wywołanie tej metody do przechowywania danych w polu określonej wartości [m_hKey](#m_hkey). Starsze wersje tej metody nie są już obsługiwane i są oznaczone jako **ATL_DEPRECATED**.  
  
```
LONG SetValue(  
    LPCTSTR pszValueName,
    DWORD dwType,
    const void* pValue,
    ULONG nBytes) throw();
    
static LONG WINAPI SetValue(  
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL);

ATL_DEPRECATED LONG SetValue(  
    DWORD dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG SetValue(  
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL,
    bool bMulti = false,
    int nValueLen = -1);
```  
  
### <a name="parameters"></a>Parametry  
 `pszValueName`  
 Wskaźnik do ciągu zawierającego nazwę wartość do ustawienia. Jeśli wartość o tej nazwie nie jest już obecne w kluczu, metoda dodaje go do klucza. Jeśli `pszValueName` ma wartość NULL lub pusty ciąg "" metoda ustawia typ i dane dla klucza bez jego nazwy lub wartość domyślna.  
  
 `dwType`  
 Określa kod wskazujący typ danych wskazywanego przez `pValue` parametru.  
  
 `pValue`  
 Wskaźnik do buforu, zawierający dane, które mają być przechowywane o nazwie określonej wartości.  
  
 `nBytes`  
 Określa rozmiar w bajtach informacji wskazywana przez `pValue` parametru. Jeśli dane są typu REG_SZ, REG_EXPAND_SZ lub REG_MULTI_SZ, `nBytes` musi zawierać rozmiar znak końcowy null.  
  
 `hKeyParent`  
 Dojście otwartego klucza.  
  
 `lpszKeyName`  
 Określa nazwę klucza do utworzenia lub otwarcia. Ta nazwa musi być podklucz `hKeyParent`.  
  
 `lpszValue`  
 Określa dane, które mają być przechowywane. Ten parametr musi mieć wartości NULL.  
  
 `lpszValueName`  
 Określa pole wartość do ustawienia. Jeśli wartość pola o tej nazwie nie istnieje już w kluczu, jest dodawany.  
  
 `dwValue`  
 Określa dane, które mają być przechowywane.  
  
 `bMulti`  
 W przypadku wartości FAŁSZ oznacza, że ten ciąg jest typu REG_SZ. Jeśli ma wartość true, wskazuje, że ten ciąg jest kolumny typu REG_MULTI_SZ.  
  
 `nValueLen`  
 Jeśli `bMulti` ma wartość true, `nValueLen` długość *lpszValue* ciąg znaków. Jeśli `bMulti` ma wartość false, wartość -1 wskazuje, że metoda obliczania długości automatycznie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie wartość niezerową błąd zdefiniowany w powiodło się. H.  
  
### <a name="remarks"></a>Uwagi  
 Dwie wersje oryginalnego `SetValue` są oznaczone jako **ATL_DEPRECATED** i nie powinna być używana. Kompilator będzie ostrzeżenie, jeśli formularze te są używane.  
  
 Trzeci wywołania metody [RegSetValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724923).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe DCOM](../../visual-cpp-samples.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
