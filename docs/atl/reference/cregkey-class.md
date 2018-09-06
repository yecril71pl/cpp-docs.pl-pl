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
ms.openlocfilehash: 75caf648b0c62827e9532fa3776def1a4e459a64
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764013"
---
# <a name="cregkey-class"></a>Klasa CRegKey

Ta klasa dostarcza metody do manipulowania wpisy w rejestrze systemowym.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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
|[CRegKey::Attach](#attach)|Wywołanie tej metody, aby dołączyć HKEY do `CRegKey` obiektu przez ustawienie [m_hKey](#m_hkey) elementu członkowskiego dojścia do `hKey`.|
|[CRegKey::Close](#close)|Wywołaj tę metodę, aby zwolnić [m_hKey](#m_hkey) elementu członkowskiego obsługi i ustaw ją na wartość NULL.|
|[CRegKey::Create](#create)|Wywołaj tę metodę, aby utworzyć określony klucz, jeśli nie istnieje jako podklucz `hKeyParent`.|
|[CRegKey::DeleteSubKey](#deletesubkey)|Wywołaj tę metodę w celu usunięcia określonego klucza z rejestru.|
|[CRegKey::DeleteValue](#deletevalue)|Wywołaj tę metodę, aby usunąć pole wartości z [m_hKey](#m_hkey).|
|[CRegKey::Detach](#detach)|Wywołanie tej metody można odłączyć [m_hKey](#m_hkey) dojście do elementu członkowskiego z `CRegKey` obiektu i ustaw `m_hKey` na wartość NULL.|
|[CRegKey::EnumKey](#enumkey)|Wywołaj tę metodę można wyliczyć podkluczy klucza rejestru Otwórz.|
|[CRegKey::Flush](#flush)|Wywołaj tę metodę, aby zapisać wszystkie atrybuty otworzyć klucza rejestru do rejestru.|
|[CRegKey::GetKeySecurity](#getkeysecurity)|Wywołaj tę metodę, aby pobrać kopię deskryptora zabezpieczeń, ochrony otworzyć klucza rejestru.|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|Ta metoda powiadamia obiekt wywołujący o zmianach wprowadzonych do atrybutów lub zawartość otworzyć klucza rejestru.|
|[CRegKey::Open](#open)|Wywołanie tej metody, aby otworzyć określony klucz i ustawić [m_hKey](#m_hkey) obsługiwać tego klucza.|
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|Wywołaj tę metodę w celu pobrania danych binarnych dla nazwy określonej wartości.|
|[CRegKey::QueryDWORDValue](#querydwordvalue)|Wywołaj tę metodę, aby pobrać dane typu DWORD nazwę określoną wartość.|
|[CRegKey::QueryGUIDValue](#queryguidvalue)|Wywołaj tę metodę w celu pobrania danych identyfikatora GUID dla nazwy określonej wartości.|
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|Wywołaj tę metodę w celu pobrania danych wielociągu nazwę określoną wartość.|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|Wywołaj tę metodę w celu pobrania danych QWORD nazwę określoną wartość.|
|[CRegKey::QueryStringValue](#querystringvalue)|Wywołaj tę metodę, aby pobrać dane ciągu dla nazwy określonej wartości.|
|[CRegKey::QueryValue](#queryvalue)|Wywołanie tej metody do pobierania danych dla określonej wartości pola [m_hKey](#m_hkey). Wcześniejszych wersjach tej metody nie są już obsługiwane i są oznaczone jako ATL_DEPRECATED.|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|Wywołaj tę metodę w celu usunięcia określonego klucza z rejestru i jawnie usunąć wszystkie podklucze.|
|[CRegKey::SetBinaryValue](#setbinaryvalue)|Wywołaj tę metodę, aby ustawić wartość binarną klucza rejestru.|
|[CRegKey::SetDWORDValue](#setdwordvalue)|Wywołaj tę metodę, aby ustawić wartość DWORD klucza rejestru.|
|[CRegKey::SetGUIDValue](#setguidvalue)|Wywołaj tę metodę, aby ustawić wartość identyfikatora GUID klucza rejestru.|
|[CRegKey::SetKeySecurity](#setkeysecurity)|Wywołaj tę metodę, aby ustawić zabezpieczenia klucza rejestru.|
|[CRegKey::SetKeyValue](#setkeyvalue)|Wywołaj tę metodę, aby przechowywać dane w polu określoną wartość z określonym kluczem.|
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|Wywołaj tę metodę można ustawić wartości wielociągu klucza rejestru.|
|[CRegKey::SetQWORDValue](#setqwordvalue)|Wywołaj tę metodę, aby ustawić wartość QWORD klucza rejestru.|
|[CRegKey::SetStringValue](#setstringvalue)|Wywołaj tę metodę, aby ustawić wartość ciągu klucza rejestru.|
|[CRegKey::SetValue](#setvalue)|Wywołanie tej metody do przechowywania danych w polu określoną wartość [m_hKey](#m_hkey). Wcześniejszych wersjach tej metody nie są już obsługiwane i są oznaczone jako ATL_DEPRECATED.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRegKey::operator HKEY](#operator_hkey)|Konwertuje `CRegKey` obiektu HKEY.|
|[CRegKey::operator =](#operator_eq)|Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|Zawiera uchwyt klucza rejestru, skojarzone z `CRegKey` obiektu.|
|[CRegKey::m_pTM](#m_ptm)|Wskaźnik do `CAtlTransactionManager` obiektu|

## <a name="remarks"></a>Uwagi

`CRegKey` zawiera metody służące do tworzenia i usuwania kluczy i wartości w rejestrze systemowym. Rejestr zawiera zestaw definicji składników systemu, takich jak numery wersji oprogramowania, mapowania logicznego na fizyczne zainstalowany sprzęt i obiekty COM specyficznych dla instalacji.

`CRegKey` udostępnia interfejs programowania do rejestru systemowego na danym komputerze. Na przykład można otworzyć klucza rejestru w szczególności, należy wywołać `CRegKey::Open`. Aby pobrać lub zmodyfikować wartość danych, należy wywołać `CRegKey::QueryValue` lub `CRegKey::SetValue`, odpowiednio. Aby zamknąć klucza, należy wywołać `CRegKey::Close`.

Po zamknięciu klucza, jego rejestru dane są zapisywane (opróżniania buforów) na dysku twardym. Ten proces może potrwać kilka sekund. Jeśli aplikacja musi jawnie zapisu danych rejestru na dysku twardym, można wywołać [RegFlushKey](/windows/desktop/api/winreg/nf-winreg-regflushkey) funkcję Win32. Jednak `RegFlushKey` używa wielu zasobów systemowych i powinna być wywoływana tylko wtedy, gdy jest to absolutnie konieczne.

> [!IMPORTANT]
>  Wszystkie metody, które umożliwiają obiektowi wywołującemu określenie lokalizacji w rejestrze ma możliwość odczytywania danych, który nie jest zaufany. Użycie metody ułatwiające wykonanie [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) należy wziąć pod uwagę, że ta funkcja nie obsługuje jawnie ciągów, które są zakończone znakiem NULL. Oba warunki powinny zostać sprawdzone przez kod wywołujący.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="attach"></a>  CRegKey::Attach

Wywołanie tej metody, aby dołączyć HKEY do `CRegKey` obiektu przez ustawienie [m_hKey](#m_hkey) elementu członkowskiego dojścia do *hKey*.

```
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>Parametry

*hKey*  
Uchwyt klucza rejestru.

### <a name="remarks"></a>Uwagi

`Attach` będzie potwierdzenia, jeśli `m_hKey` jest różna od NULL.

##  <a name="close"></a>  CRegKey::Close

Wywołaj tę metodę, aby zwolnić [m_hKey](#m_hkey) elementu członkowskiego obsługi i ustaw ją na wartość NULL.

```
LONG Close() throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie zwraca wartość błędu.

##  <a name="create"></a>  CRegKey::Create

Wywołaj tę metodę, aby utworzyć określony klucz, jeśli nie istnieje jako podklucz *hKeyParent*.

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

*hKeyParent*  
Dojście otwartego klucza.

*lpszKeyName*  
Określa nazwę klucza, który ma zostać utworzony lub otwarty. Ta nazwa musi być podklucz *hKeyParent*.

*lpszClass*  
Określa klasę klucza, który ma zostać utworzony lub otwarty. Wartość domyślna to REG_NONE.

*dwOptions*  
Opcje dla klucza. Wartość domyślna to REG_OPTION_NON_VOLATILE. Aby uzyskać listę możliwych wartości i opisy, zobacz [RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) w zestawie Windows SDK.

*samDesired*  
Zabezpieczeń dostępu do klucza. Wartość domyślna to KEY_READ &#124; KEY_WRITE. Aby uzyskać listę możliwych wartości i opisy, zobacz `RegCreateKeyEx`.

*lpSecAttr*  
Wskaźnik do [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) strukturę, która wskazuje, czy uchwyt klucza może być dziedziczona przez proces podrzędny. Domyślnie ten parametr ma wartość NULL (znaczenie, który nie może być dziedziczona uchwyt).

*lpdwDisposition*  
[out] Jeśli innych niż NULL, pobiera REG_CREATED_NEW_KEY (Jeśli klucz nie istnieje i został utworzony) lub REG_OPENED_EXISTING_KEY (Jeśli klucz istniał i został otwarty).

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca ERROR_SUCCESS i otwiera klucza. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowany w powiodło się. kod błędu różny od zera. H.

### <a name="remarks"></a>Uwagi

`Create` Ustawia [m_hKey](#m_hkey) elementu członkowskiego do realizacji tego klucza.

##  <a name="cregkey"></a>  CRegKey::CRegKey

Konstruktor.

```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```

### <a name="parameters"></a>Parametry

*Klucz*  
Odwołanie do `CRegKey` obiektu.

*hKey*  
Dojście do klucza rejestru.

*pTM*  
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

Tworzy nową `CRegKey` obiektu. Obiekt można tworzyć na podstawie istniejącego `CRegKey` obiektu lub dojście do klucza rejestru.

##  <a name="dtor"></a>  CRegKey:: ~ CRegKey

Destruktor.

```
~CRegKey() throw();
```

### <a name="remarks"></a>Uwagi

Wersje destruktor `m_hKey`.

##  <a name="deletesubkey"></a>  CRegKey::DeleteSubKey

Wywołaj tę metodę w celu usunięcia określonego klucza z rejestru.

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>Parametry

*lpszSubKey*  
Określa nazwę klucza do usunięcia. Ta nazwa musi być podklucz [m_hKey](#m_hkey).

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowany w powiodło się. kod błędu różny od zera. H.

### <a name="remarks"></a>Uwagi

`DeleteSubKey` usunąć można tylko klucz, który ma nie kluczy podrzędnych. Jeśli klucz ma podklucze, wywołaj [RecurseDeleteKey](#recursedeletekey) zamiast tego.

##  <a name="deletevalue"></a>  CRegKey::DeleteValue

Wywołaj tę metodę, aby usunąć pole wartości z [m_hKey](#m_hkey).

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>Parametry

*lpszValue*  
Określa pole wartości do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowany w powiodło się. kod błędu różny od zera. H.

##  <a name="detach"></a>  CRegKey::Detach

Wywołanie tej metody można odłączyć [m_hKey](#m_hkey) dojście do elementu członkowskiego z `CRegKey` obiektu i ustaw `m_hKey` na wartość NULL.

```
HKEY Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

HKEY skojarzone z `CRegKey` obiektu.

##  <a name="enumkey"></a>  CRegKey::EnumKey

Wywołaj tę metodę można wyliczyć podkluczy klucza rejestru Otwórz.

```
LONG EnumKey(  
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>Parametry

*iIndex*  
Indeks podklucza. Ten parametr powinna wynosić zero dla pierwszego wywołania i następnie są zwiększane dla kolejnych wywołań

*pszName*  
Wskaźnik do buforu, który otrzymuje nazwę podklucza, w tym kończącego znaku null. Nazwa podklucza który jest kopiowany do buforu, a nie pełne kluczowej hierarchii.

*pnNameLength*  
Wskaźnik do zmiennej, która określa rozmiar w TCHARs buforu określony przez *pszName* parametru. Ten rozmiar powinien zawierać kończącego znaku null. Gdy metoda zwróci wartość, zmienna wskazywany przez *pnNameLength* zawiera liczbę znaków przechowywanych w buforze. Liczba zwracane nie obejmuje kończącego znaku null.

*pftLastWriteTime*  
Wskaźnik do zmiennej, która odbiera czas ostatniego zapisania podklucz wyliczany do.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowany w powiodło się. kod błędu różny od zera. H.

### <a name="remarks"></a>Uwagi

Aby wyliczyć podkluczy, należy wywołać `CRegKey::EnumKey` o indeksie zero. Zwiększ wartość indeksu, a następnie powtórz, metoda zwraca ERROR_NO_MORE_ITEMS. Aby uzyskać więcej informacji, zobacz [RegEnumKeyEx](/windows/desktop/api/winreg/nf-winreg-regenumkeyexa) w zestawie Windows SDK.

##  <a name="flush"></a>  CRegKey::Flush

Wywołaj tę metodę, aby zapisać wszystkie atrybuty otworzyć klucza rejestru do rejestru.

```
LONG Flush() throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowany w powiodło się. kod błędu różny od zera. H.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [RegEnumFlush](/windows/desktop/api/winreg/nf-winreg-regflushkey) w zestawie Windows SDK.

##  <a name="getkeysecurity"></a>  CRegKey::GetKeySecurity

Wywołaj tę metodę, aby pobrać kopię deskryptora zabezpieczeń, ochrony otworzyć klucza rejestru.

```
LONG GetKeySecurity(  
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>Parametry

*SI*  
[SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) wartość, która wskazuje żądane informacje o zabezpieczeniach.

*PSD*  
Wskaźnik do buforu, który otrzymuje kopię deskryptora zabezpieczeń żądanej.

*pnBytes*  
Rozmiar w bajtach, bufor wskazywany przez *psd*.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest, że zdefiniowano powiodło się. kod błędu różny od zera. H.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [RegGetKeySecurity](/windows/desktop/api/winreg/nf-winreg-reggetkeysecurity).

##  <a name="m_hkey"></a>  CRegKey::m_hKey

Zawiera uchwyt klucza rejestru, skojarzone z `CRegKey` obiektu.

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

Ta metoda powiadamia obiekt wywołujący o zmianach wprowadzonych do atrybutów lub zawartość otworzyć klucza rejestru.

```
LONG NotifyChangeKeyValue(  
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bWatchSubtree*  
Określa flagi, która wskazuje, czy do zgłaszania zmian w określonym kluczu i wszystkich jego podkluczy lub tylko określonego klucza. Jeśli ten parametr ma wartość TRUE, metoda zgłasza zmian w kluczu i jego podkluczach. Jeśli parametr ma wartość FALSE, metoda zgłasza zmiany tylko w kluczu.

*dwNotifyFilter*  
Określa, że zestaw flag, które kontrolują, które zmiany powinny być raportowane. Ten parametr może być kombinacją następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|Powiadomić obiekt wywołujący, jeśli podklucz zostanie dodany lub usunięty.|
|REG_NOTIFY_CHANGE_ATTRIBUTES|Powiadamia obiekt wywołujący zmiany atrybutów klucza, takie jak informacje deskryptora zabezpieczeń.|
|REG_NOTIFY_CHANGE_LAST_SET|Powiadamia obiekt wywołujący zmiana wartości klucza. Może to obejmować dodawanie lub usuwanie wartości lub zmianę istniejącej wartości.|
|REG_NOTIFY_CHANGE_SECURITY|Powiadamia obiekt wywołujący zmiany deskryptor zabezpieczeń klucza.|

*hEvent*  
Obsłuż to zdarzenie. Jeśli *bAsync* parametr ma wartość TRUE, metoda zwraca natychmiast, a zmiany są zgłaszane przez sygnalizowanie tego zdarzenia. Jeśli *bAsync* ma wartość FAŁSZ, *hEvent* jest ignorowana.

*bAsync*  
Określa flagi, która wskazuje, jak metoda raporty zmiany. Jeśli ten parametr ma wartość TRUE, metoda zwraca niezwłocznie i raporty zmiany przez sygnalizowanie określonego zdarzenia. Jeśli ten parametr ma wartość FALSE, metoda nie zwraca do momentu zostało zmienione. Jeśli *hEvent* nie określa ważnego zdarzenia *bAsync* parametr nie może mieć wartość TRUE.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowany w powiodło się. kod błędu różny od zera. H.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Ta metoda nie powoduje powiadomienia obiekt wywołujący, jeśli określony klucz zostanie usunięty.

Aby uzyskać więcej informacji i przykładowy program, zobacz [wywołanie funkcji RegNotifyChangeKeyValue](/windows/desktop/api/winreg/nf-winreg-regnotifychangekeyvalue).

##  <a name="open"></a>  CRegKey::Open

Wywołanie tej metody, aby otworzyć określony klucz i ustawić [m_hKey](#m_hkey) obsługiwać tego klucza.

```
LONG Open(  
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>Parametry

*hKeyParent*  
Dojście otwartego klucza.

*lpszKeyName*  
Określa nazwę klucza, który ma zostać utworzony lub otwarty. Ta nazwa musi być podklucz *hKeyParent*.

*samDesired*  
Zabezpieczeń dostępu do klucza. Wartość domyślna to KEY_ALL_ACCESS. Aby uzyskać listę możliwych wartości i opisy, zobacz [RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie wartość błędu różny od zera jest zdefiniowany w powiodło się. H.

### <a name="remarks"></a>Uwagi

Jeśli *lpszKeyName* parametr ma wartość NULL lub punktów do pustego ciągu, `Open` zostanie otwarty nowy uchwyt klucza identyfikowane przez *hKeyParent*, ale nie zamyka wszystkie wcześniej otwarte dojście.

W odróżnieniu od [CRegKey::Create](#create), `Open` nie utworzy określony klucz, jeśli nie istnieje.

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

*Klucz*  
Klucz do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do nowego klucza.

### <a name="remarks"></a>Uwagi

Ten operator odłącza *klucz* z jej bieżącego obiektu i przypisuje go do `CRegKey` zamiast tego obiektu.

##  <a name="querybinaryvalue"></a>  CRegKey::QueryBinaryValue

Wywołaj tę metodę w celu pobrania danych binarnych dla nazwy określonej wartości.

```
LONG QueryBinaryValue(  
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*  
Wskaźnik na ciąg zakończony wartością null zawierający nazwę wartości do zapytania.

*pValue*  
Wskaźnik do buforu, który odbiera dane z tej wartości.

*pnBytes*  
Wskaźnik do zmiennej, która określa rozmiar w bajtach, bufor wskazywany przez *pValue* parametru. Gdy metoda zwróci wartość, ta zmienna uwzględnia rozmiar danych skopiowane do buforu.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwracany jest ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca zdefiniowane w powiodło się. kod błędu różny od zera. H. Jeśli dane przywoływane nie jest typu REG_BINARY, zwracany jest ERROR_INVALID_DATA.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta z `RegQueryValueEx` i potwierdza, że zwracany jest poprawny typ danych. Zobacz [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) Aby uzyskać więcej informacji.

> [!IMPORTANT]
>  Ta metoda umożliwia obiektowi wywołującemu określenie dowolnej lokalizacji w rejestrze, potencjalny Odczyt danych, który nie jest zaufany. Ponadto [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) funkcja używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone znakiem NULL. Oba warunki powinny zostać sprawdzone przez kod wywołujący.

##  <a name="querydwordvalue"></a>  CRegKey::QueryDWORDValue

Wywołaj tę metodę, aby pobrać dane typu DWORD nazwę określoną wartość.

```
LONG QueryDWORDValue(  
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*  
Wskaźnik na ciąg zakończony wartością null zawierający nazwę wartości do zapytania.

*dwValue*  
Wskaźnik do buforu, który otrzymuje wartości DWORD.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwracany jest ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca zdefiniowane w powiodło się. kod błędu różny od zera. H. Jeśli dane przywoływane nie jest typu REG_DWORD, zwracany jest ERROR_INVALID_DATA.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta z `RegQueryValueEx` i potwierdza, że zwracany jest poprawny typ danych. Zobacz [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) Aby uzyskać więcej informacji.

> [!IMPORTANT]
>  Ta metoda umożliwia obiektowi wywołującemu określenie dowolnej lokalizacji w rejestrze, potencjalny Odczyt danych, który nie jest zaufany. Ponadto [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) funkcja używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone znakiem NULL. Oba warunki powinny zostać sprawdzone przez kod wywołujący.

##  <a name="queryguidvalue"></a>  CRegKey::QueryGUIDValue

Wywołaj tę metodę w celu pobrania danych identyfikatora GUID dla nazwy określonej wartości.

```
LONG QueryGUIDValue(  
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*  
Wskaźnik na ciąg zakończony wartością null zawierający nazwę wartości do zapytania.

*guidValue*  
Wskaźnik do zmiennej, która odbiera identyfikator GUID.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwracany jest ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca zdefiniowane w powiodło się. kod błędu różny od zera. H. Jeśli dane przywoływane nie jest prawidłowym identyfikatorem GUID, zwracany jest ERROR_INVALID_DATA.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta z `CRegKey::QueryStringValue` i konwertuje ciąg na identyfikator GUID za pomocą [CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring).

> [!IMPORTANT]
>  Ta metoda umożliwia obiektowi wywołującemu określenie dowolnej lokalizacji w rejestrze, potencjalny Odczyt danych, który nie jest zaufany.

##  <a name="querymultistringvalue"></a>  CRegKey::QueryMultiStringValue

Wywołaj tę metodę w celu pobrania danych wielociągu nazwę określoną wartość.

```
LONG QueryMultiStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*  
Wskaźnik na ciąg zakończony wartością null zawierający nazwę wartości do zapytania.

*pszValue*  
Wskaźnik do buforu, który odbiera dane wielociągu. FixedLength jest tablicą ciągów zakończony znakiem null, został przerwany przez dwa znaki o wartości null.

*pnChars*  
Rozmiar w TCHARs buforu wskazywany przez *pszValue*. Po powrocie z metody *pnChars* zawiera rozmiar w TCHARs z FixedLength pobierane, w tym kończącego znaku null.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwracany jest ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca zdefiniowane w powiodło się. kod błędu różny od zera. H. Jeśli dane przywoływane nie jest typu REG_MULTI_SZ, zwracany jest ERROR_INVALID_DATA.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta z `RegQueryValueEx` i potwierdza, że zwracany jest poprawny typ danych. Zobacz [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) Aby uzyskać więcej informacji.

> [!IMPORTANT]
>  Ta metoda umożliwia obiektowi wywołującemu określenie dowolnej lokalizacji w rejestrze, potencjalny Odczyt danych, który nie jest zaufany. Ponadto [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) funkcja używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone znakiem NULL. Oba warunki powinny zostać sprawdzone przez kod wywołujący.

##  <a name="queryqwordvalue"></a>  CRegKey::QueryQWORDValue

Wywołaj tę metodę w celu pobrania danych QWORD nazwę określoną wartość.

```
LONG QueryQWORDValue(  
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*  
Wskaźnik na ciąg zakończony wartością null zawierający nazwę wartości do zapytania.

*qwValue*  
Wskaźnik do buforu, który otrzymuje QWORD.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwracany jest ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca zdefiniowane w powiodło się. kod błędu różny od zera. H. Jeśli dane przywoływane nie jest typu REG_QWORD, zwracany jest ERROR_INVALID_DATA.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta z `RegQueryValueEx` i potwierdza, że zwracany jest poprawny typ danych. Zobacz [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) Aby uzyskać więcej informacji.

> [!IMPORTANT]
>  Ta metoda umożliwia obiektowi wywołującemu określenie dowolnej lokalizacji w rejestrze, potencjalny Odczyt danych, który nie jest zaufany. Ponadto [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) funkcja używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone znakiem NULL. Oba warunki powinny zostać sprawdzone przez kod wywołujący.

##  <a name="querystringvalue"></a>  CRegKey::QueryStringValue

Wywołaj tę metodę, aby pobrać dane ciągu dla nazwy określonej wartości.

```
LONG QueryStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*  
Wskaźnik na ciąg zakończony wartością null zawierający nazwę wartości do zapytania.

*pszValue*  
Wskaźnik do buforu, który odbiera dane ciągu.

*pnChars*  
Rozmiar w TCHARs buforu wskazywany przez *pszValue*. Po powrocie z metody *pnChars* zawiera rozmiar w TCHARs ciągu pobierane, w tym kończącego znaku null.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, zwracany jest ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca zdefiniowane w powiodło się. kod błędu różny od zera. H. Jeśli dane przywoływane nie jest typu REG_SZ, zwracany jest ERROR_INVALID_DATA. Jeśli metoda zwraca kod ERROR_MORE_DATA, *pnChars* jest równa zero nie wymagany rozmiar buforu w bajtach.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta z `RegQueryValueEx` i potwierdza, że zwracany jest poprawny typ danych. Zobacz [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) Aby uzyskać więcej informacji.

> [!IMPORTANT]
>  Ta metoda umożliwia obiektowi wywołującemu określenie dowolnej lokalizacji w rejestrze, potencjalny Odczyt danych, który nie jest zaufany. Ponadto [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) funkcja używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone znakiem NULL. Oba warunki powinny zostać sprawdzone przez kod wywołujący.

##  <a name="queryvalue"></a>  CRegKey::QueryValue

Wywołanie tej metody do pobierania danych dla określonej wartości pola [m_hKey](#m_hkey). Wcześniejszych wersjach tej metody nie są już obsługiwane i są oznaczone jako ATL_DEPRECATED.

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

*pszValueName*  
Wskaźnik na ciąg zakończony wartością null zawierający nazwę wartości do zapytania. Jeśli *pszValueName* ma wartość NULL lub pustym ciągiem, "" metoda pobiera typ i danych dla klucza użytkownika nienazwane lub wartość domyślna, jeśli istnieje.

*pdwType*  
Wskaźnik do zmiennej, która odbiera kod, wskazujący typ danych przechowywanych na określoną wartość. *PdwType* parametr może mieć wartość NULL, jeśli kod typu nie jest wymagana.

*pData*  
Wskaźnik do buforu, który odbiera dane z tej wartości. Ten parametr może być wartością NULL, jeśli dane nie jest wymagana.

*pnBytes*  
Wskaźnik do zmiennej, która określa rozmiar w bajtach, bufor wskazywany przez *pData* parametru. Gdy metoda zwróci wartość, ta zmienna uwzględnia rozmiar danych skopiowane do *pData.*

*dwValue*  
Pole wartości danych liczbowych.

*lpszValueName*  
Określa wartość pola można wykonywać zapytania.

*szValue*  
Dane ciągu w polu wartość.

*pdwCount*  
Rozmiar danych ciągu. Jego wartość jest początkowo ustawiona do rozmiaru *szValue* buforu.

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie kod błędu różny od zera jest zdefiniowany w powiodło się. H.

### <a name="remarks"></a>Uwagi

Dwie wersje oryginalnego `QueryValue` nie są już obsługiwane i są oznaczone jako ATL_DEPRECATED. Kompilator zgłosi ostrzeżenie, jeśli używane są te formularze.

Pozostałe wywołania metody RegQueryValueEx.

> [!IMPORTANT]
>  Ta metoda umożliwia obiektowi wywołującemu określenie dowolnej lokalizacji w rejestrze, potencjalny Odczyt danych, który nie jest zaufany. Ponadto funkcja RegQueryValueEx używane przez tę metodę nie obsługuje jawnie ciągów, które są zakończone znakiem NULL. Oba warunki powinny zostać sprawdzone przez kod wywołujący.

##  <a name="recursedeletekey"></a>  CRegKey::RecurseDeleteKey

Wywołaj tę metodę w celu usunięcia określonego klucza z rejestru i jawnie usunąć wszystkie podklucze.

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>Parametry

*lpszKey*  
Określa nazwę klucza do usunięcia. Ta nazwa musi być podklucz [m_hKey](#m_hkey).

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie wartość błędu różny od zera jest zdefiniowany w powiodło się. H.

### <a name="remarks"></a>Uwagi

Jeśli klucz ma podklucze, należy wywołać tę metodę w celu usunięcia klucza.

##  <a name="setbinaryvalue"></a>  CRegKey::SetBinaryValue

Wywołaj tę metodę, aby ustawić wartość binarną klucza rejestru.

```
LONG SetBinaryValue(  
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*  
Wskaźnik do ciągu zawierającego nazwę wartości do ustawienia. Jeśli wartość z tą nazwą nie jest już obecny, metoda dodaje ją do klucza.

*pValue*  
Wskaźnik do buforu, zawierające dane, które mają być przechowywane z wartością o określonej nazwie.

*nBytes*  
Określa rozmiar w bajtach informacji wskazywany przez *pValue* parametru.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowany w powiodło się. kod błędu różny od zera. H.

### <a name="remarks"></a>Uwagi

Ta metoda używa [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) do zapisu wartości w rejestrze.

##  <a name="setdwordvalue"></a>  CRegKey::SetDWORDValue

Wywołaj tę metodę, aby ustawić wartość DWORD klucza rejestru.

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*  
Wskaźnik do ciągu zawierającego nazwę wartości do ustawienia. Jeśli wartość z tą nazwą nie jest już obecny, metoda dodaje ją do klucza.

*dwValue*  
Dane typu DWORD, które mają być przechowywane z wartością o określonej nazwie.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowany w powiodło się. kod błędu różny od zera. H.

### <a name="remarks"></a>Uwagi

Ta metoda używa [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) do zapisu wartości w rejestrze.

##  <a name="setguidvalue"></a>  CRegKey::SetGUIDValue

Wywołaj tę metodę, aby ustawić wartość identyfikatora GUID klucza rejestru.

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*  
Wskaźnik do ciągu zawierającego nazwę wartości do ustawienia. Jeśli wartość z tą nazwą nie jest już obecny, metoda dodaje ją do klucza.

*guidValue*  
Odwołanie do identyfikatora GUID, które mają być przechowywane z wartością o określonej nazwie.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowany w powiodło się. kod błędu różny od zera. H.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta z `CRegKey::SetStringValue` i konwertuje ciąg za pomocą identyfikatora GUID [StringFromGUID2](/windows/desktop/api/combaseapi/nf-combaseapi-stringfromguid2).

##  <a name="setkeyvalue"></a>  CRegKey::SetKeyValue

Wywołaj tę metodę, aby przechowywać dane w polu określoną wartość z określonym kluczem.

```
LONG SetKeyValue(  
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>Parametry

*lpszKeyName*  
Określa nazwę klucza, który ma zostać utworzony lub otwarty. Ta nazwa musi być podklucz [m_hKey](#m_hkey).

*lpszValue*  
Określa dane, które mają być przechowywane. Ten parametr musi być inna niż NULL.

*lpszValueName*  
Określa pole wartości do ustawienia. Jeśli wartość pola o tej nazwie już istnieje w kluczu, zostanie dodany.

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie kod błędu różny od zera jest zdefiniowany w powiodło się. H.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby utworzyć lub otworzyć *lpszKeyName* klucza i przechowywać *lpszValue* dane w *lpszValueName* pole wartości.

##  <a name="setkeysecurity"></a>  CRegKey::SetKeySecurity

Wywołaj tę metodę, aby ustawić zabezpieczenia klucza rejestru.

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>Parametry

*SI*  
Określa składniki, które można ustawić deskryptora zabezpieczeń. Wartość może być kombinacją następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|Ustawia klucz poufnej-listy kontroli dostępu (DACL). Klucz musi mieć dostęp WRITE_DAC lub proces wywołujący musi być właścicielem obiektu.|
|GROUP_SECURITY_INFORMATION|Ustawia identyfikator zabezpieczeń grupy podstawowej klucza (SID). Klucz musi mieć dostęp WRITE_OWNER lub proces wywołujący musi być właścicielem obiektu.|
|OWNER_SECURITY_INFORMATION|Ustawia identyfikator SID właściciela klucza. Klucz musi mieć dostęp WRITE_OWNER lub proces wywołujący musi być właścicielem obiektu lub mieć włączone uprawnienie SE_TAKE_OWNERSHIP_NAME.|
|SACL_SECURITY_INFORMATION|Ustawia listy kontroli dostępu systemu klucza (SACL). Klucz musi mieć dostęp ACCESS_SYSTEM_SECURITY. Odpowiednie sposobem uzyskania takiego dostępu jest umożliwienie SE_SECURITY_NAME [uprawnień](https://msdn.microsoft.com/library/windows/desktop/aa379306) w bieżącym tokenu dostępu obiektu wywołującego, otworzyć uchwytu ACCESS_SYSTEM_SECURITY dostępu, a następnie wyłącz uprawnienia.|

*PSD*  
Wskaźnik do [SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor) strukturę, która określa atrybuty zabezpieczeń, aby ustawić dla określonego klucza.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowany w powiodło się. kod błędu różny od zera. H.

### <a name="remarks"></a>Uwagi

Ustawia atrybuty zabezpieczeń klucza. Zobacz [RegSetKeySecurity](/windows/desktop/api/winreg/nf-winreg-regsetkeysecurity) Aby uzyskać więcej informacji.

##  <a name="setmultistringvalue"></a>  CRegKey::SetMultiStringValue

Wywołaj tę metodę można ustawić wartości wielociągu klucza rejestru.

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*  
Wskaźnik do ciągu zawierającego nazwę wartości do ustawienia. Jeśli wartość z tą nazwą nie jest już obecny, metoda dodaje ją do klucza.

*pszValue*  
Wskaźnik do wielociągu dane, które mają być przechowywane z wartością o określonej nazwie. FixedLength jest tablicą ciągów zakończony znakiem null, został przerwany przez dwa znaki o wartości null.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowany w powiodło się. kod błędu różny od zera. H.

### <a name="remarks"></a>Uwagi

Ta metoda używa [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) do zapisu wartości w rejestrze.

##  <a name="setqwordvalue"></a>  CRegKey::SetQWORDValue

Wywołaj tę metodę, aby ustawić wartość QWORD klucza rejestru.

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*  
Wskaźnik do ciągu zawierającego nazwę wartości do ustawienia. Jeśli wartość z tą nazwą nie jest już obecny, metoda dodaje ją do klucza.

*qwValue*  
QWORD dane mają być przechowywane z wartością o określonej nazwie.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowany w powiodło się. kod błędu różny od zera. H.

### <a name="remarks"></a>Uwagi

Ta metoda używa [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) do zapisu wartości w rejestrze.

##  <a name="setstringvalue"></a>  CRegKey::SetStringValue

Wywołaj tę metodę, aby ustawić wartość ciągu klucza rejestru.

```
LONG SetStringValue(  
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*  
Wskaźnik do ciągu zawierającego nazwę wartości do ustawienia. Jeśli wartość z tą nazwą nie jest już obecny, metoda dodaje ją do klucza.

*pszValue*  
Wskaźnik do danych ciągu, które mają być przechowywane z wartością o określonej nazwie.

*dwType*  
Typ ciągu do zapisu w rejestrze: REG_SZ (ustawienie domyślne) lub REG_EXPAND_SZ (do multistrings).

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, wartość zwracana jest zdefiniowany w powiodło się. kod błędu różny od zera. H.

### <a name="remarks"></a>Uwagi

Ta metoda używa [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) do zapisu wartości w rejestrze.

##  <a name="setvalue"></a>  CRegKey::SetValue

Wywołanie tej metody do przechowywania danych w polu określoną wartość [m_hKey](#m_hkey). Wcześniejszych wersjach tej metody nie są już obsługiwane i są oznaczone jako ATL_DEPRECATED.

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

*pszValueName*  
Wskaźnik do ciągu zawierającego nazwę wartości do ustawienia. Jeśli wartość z tą nazwą nie jest już obecne w kluczu, metoda dodaje ją do klucza. Jeśli *pszValueName* ma wartość NULL lub pustym ciągiem, "" metoda ustawia typ i danych dla klucza użytkownika nienazwane lub wartość domyślna.

*dwType*  
Określa kod, wskazujący typ danych, do których prowadzą *pValue* parametru.

*pValue*  
Wskaźnik do buforu, zawierające dane, które mają być przechowywane z wartością o określonej nazwie.

*nBytes*  
Określa rozmiar w bajtach informacji wskazywany przez *pValue* parametru. Jeśli dane są typu REG_SZ, REG_EXPAND_SZ lub REG_MULTI_SZ, *nBytes* musi zawierają rozmiaru kończącego znaku null.

*hKeyParent*  
Dojście otwartego klucza.

*lpszKeyName*  
Określa nazwę klucza, który ma zostać utworzony lub otwarty. Ta nazwa musi być podklucz *hKeyParent*.

*lpszValue*  
Określa dane, które mają być przechowywane. Ten parametr musi być inna niż NULL.

*lpszValueName*  
Określa pole wartości do ustawienia. Jeśli wartość pola o tej nazwie już istnieje w kluczu, zostanie dodany.

*dwValue*  
Określa dane, które mają być przechowywane.

*bMulti*  
W przypadku wartości FAŁSZ oznacza, że ten ciąg jest typu REG_SZ. W przypadku opcji true wskazuje, że ten ciąg jest FixedLength typu REG_MULTI_SZ.

*nValueLen*  
Jeśli *bMulti* ma wartość true, *nValueLen* jest długością *lpszValue* ciąg znaków. Jeśli *bMulti* ma wartość false, wartość -1 wskazuje, że metoda oblicza długość automatycznie.

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie kod błędu różny od zera jest zdefiniowany w powiodło się. H.

### <a name="remarks"></a>Uwagi

Dwie wersje oryginalnego `SetValue` są oznaczone jako ATL_DEPRECATED i już nie powinny być używane. Kompilator zgłosi ostrzeżenie, jeśli używane są te formularze.

Trzeci wywołania metody [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa).

## <a name="see-also"></a>Zobacz też

[Przykładowy model DCOM](../../visual-cpp-samples.md)   
[Klasa — Przegląd](../../atl/atl-class-overview.md)
