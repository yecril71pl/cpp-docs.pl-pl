---
title: Klasa CRegKey
ms.date: 11/04/2016
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
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
ms.openlocfilehash: bce5a16dd8d6564b6a0d3fa0344fe5cb2303764f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915791"
---
# <a name="cregkey-class"></a>Klasa CRegKey

Ta klasa zawiera metody manipulowania wpisami w rejestrze systemowym.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CRegKey
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRegKey:: CRegKey](#cregkey)|Konstruktor.|
|[CRegKey:: ~ CRegKey](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRegKey:: Attach](#attach)|Wywołaj tę metodę, aby dołączyć HKEY do `CRegKey` obiektu przez ustawienie uchwytu elementu członkowskiego `hKey` [m_hKey](#m_hkey) na.|
|[CRegKey:: Close](#close)|Wywołaj tę metodę, aby zwolnić uchwyt składowej [m_hKey](#m_hkey) i ustawić na wartość null.|
|[CRegKey:: Create](#create)|Wywołaj tę metodę, aby utworzyć określony klucz, jeśli nie istnieje jako podklucz `hKeyParent`.|
|[CRegKey::DeleteSubKey](#deletesubkey)|Wywołaj tę metodę, aby usunąć określony klucz z rejestru.|
|[CRegKey::D eleteValue](#deletevalue)|Wywołaj tę metodę, aby usunąć pole wartości z [m_hKey](#m_hkey).|
|[CRegKey::D etach](#detach)|Wywołaj tę metodę, aby [](#m_hkey) odłączyć uchwyt składowej m_hKey `CRegKey` z obiektu i `m_hKey` ustawić na wartość null.|
|[CRegKey:: EnumKey](#enumkey)|Wywołaj tę metodę, aby wyliczyć podklucze otwartego klucza rejestru.|
|[CRegKey:: Flush](#flush)|Wywołaj tę metodę, aby zapisać wszystkie atrybuty otwartego klucza rejestru w rejestrze.|
|[CRegKey:: GetKeySecurity](#getkeysecurity)|Wywołaj tę metodę, aby pobrać kopię deskryptora zabezpieczeń chroniącą otwarty klucz rejestru.|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|Ta metoda powiadamia obiekt wywołujący o zmianach atrybutów lub zawartości otwartego klucza rejestru.|
|[CRegKey:: Open](#open)|Wywołaj tę metodę, aby otworzyć określony klucz i ustawić [m_hKey](#m_hkey) na dojście tego klucza.|
|[CRegKey:: QueryBinaryValue](#querybinaryvalue)|Wywołaj tę metodę, aby pobrać dane binarne dla określonej nazwy wartości.|
|[CRegKey:: QueryDWORDValue](#querydwordvalue)|Wywołaj tę metodę, aby pobrać dane DWORD dla określonej nazwy wartości.|
|[CRegKey:: QueryGUIDValue](#queryguidvalue)|Wywołaj tę metodę, aby pobrać dane identyfikatora GUID dla określonej nazwy wartości.|
|[CRegKey:: QueryMultiStringValue](#querymultistringvalue)|Wywołaj tę metodę, aby pobrać dane z wielociągu dla określonej nazwy wartości.|
|[CRegKey:: QueryQWORDValue](#queryqwordvalue)|Wywołaj tę metodę, aby pobrać dane QWORD dla określonej nazwy wartości.|
|[CRegKey:: QueryStringValue](#querystringvalue)|Wywołaj tę metodę, aby pobrać dane ciągu dla określonej nazwy wartości.|
|[CRegKey:: QueryValue](#queryvalue)|Wywołaj tę metodę, aby pobrać dane dla określonego pola wartości [m_hKey](#m_hkey). Wcześniejsze wersje tej metody nie są już obsługiwane i są oznaczone jako ATL_DEPRECATED.|
|[CRegKey:: RecurseDeleteKey](#recursedeletekey)|Wywołaj tę metodę, aby usunąć określony klucz z rejestru i jawnie usunąć wszystkie podklucze.|
|[CRegKey:: SetBinaryValue](#setbinaryvalue)|Wywołaj tę metodę, aby ustawić wartość binarną klucza rejestru.|
|[CRegKey:: SetDWORDValue](#setdwordvalue)|Wywołaj tę metodę, aby ustawić wartość DWORD klucza rejestru.|
|[CRegKey:: SetGUIDValue](#setguidvalue)|Wywołaj tę metodę, aby ustawić wartość identyfikatora GUID klucza rejestru.|
|[CRegKey:: SetKeySecurity](#setkeysecurity)|Wywołaj tę metodę, aby ustawić zabezpieczenia klucza rejestru.|
|[CRegKey:: SetKeyValue](#setkeyvalue)|Wywołaj tę metodę, aby przechowywać dane w określonym polu wartości określonego klucza.|
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|Wywołaj tę metodę, aby ustawić wartość wielociągową klucza rejestru.|
|[CRegKey:: SetQWORDValue](#setqwordvalue)|Wywołaj tę metodę, aby ustawić wartość QWORD klucza rejestru.|
|[CRegKey:: SetStringValue](#setstringvalue)|Wywołaj tę metodę, aby ustawić wartość ciągu klucza rejestru.|
|[CRegKey:: SetValue](#setvalue)|Wywołaj tę metodę, aby przechowywać dane w określonym polu wartości [m_hKey](#m_hkey). Wcześniejsze wersje tej metody nie są już obsługiwane i są oznaczone jako ATL_DEPRECATED.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRegKey:: operator HKEY](#operator_hkey)|`CRegKey` Konwertuje obiekt na HKEY.|
|[CRegKey:: operator =](#operator_eq)|Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|Zawiera dojście klucza rejestru skojarzonego z `CRegKey` obiektem.|
|[CRegKey::m_pTM](#m_ptm)|Wskaźnik do `CAtlTransactionManager` obiektu|

## <a name="remarks"></a>Uwagi

`CRegKey`zapewnia metody tworzenia i usuwania kluczy oraz wartości w rejestrze systemowym. Rejestr zawiera zestaw definicji dla składników systemowych, takich jak numery wersji oprogramowania, mapowania logiczne-do-fizycznego zainstalowanego sprzętu i obiekty COM.

`CRegKey`zapewnia interfejs programowania dla rejestru systemowego dla danego komputera. Na przykład, aby otworzyć określony klucz rejestru, wywołaj `CRegKey::Open`polecenie. Aby pobrać lub zmodyfikować wartość danych, wywołaj `CRegKey::QueryValue` lub `CRegKey::SetValue`, odpowiednio. Aby zamknąć klucz, wywołaj `CRegKey::Close`polecenie.

Po zamknięciu klucza jego dane rejestru są zapisywane (opróżniane) na dysku twardym. Ten proces może potrwać kilka sekund. Jeśli aplikacja musi jawnie zapisywać dane rejestru na dysku twardym, można wywołać funkcję Win32 [podczas operacji RegFlushKey](/windows/desktop/api/winreg/nf-winreg-regflushkey) . Jednak program `RegFlushKey` używa wielu zasobów systemowych i powinien być wywoływany tylko w razie absolutnej konieczności.

> [!IMPORTANT]
>  Wszelkie metody, które umożliwiają obiektowi wywołującemu określenie lokalizacji w rejestrze, mają możliwość odczytywania danych, które nie mogą być zaufane. Metody, które korzystają z [działanie funkcji RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) należy wziąć pod uwagę, że ta funkcja nie obsługuje jawnie ciągów, które są zakończone wartością null. Kod wywołujący musi być sprawdzony dla obu warunków.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

##  <a name="attach"></a>CRegKey:: Attach

Wywołaj tę metodę, aby dołączyć HKEY do `CRegKey` obiektu przez ustawienie uchwytu elementu członkowskiego [m_hKey](#m_hkey) na *HKEY*.

```
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Dojście klucza rejestru.

### <a name="remarks"></a>Uwagi

`Attach`zostanie potwierdzone, `m_hKey` Jeśli ma wartość różną od null.

##  <a name="close"></a>CRegKey:: Close

Wywołaj tę metodę, aby zwolnić uchwyt składowej [m_hKey](#m_hkey) i ustawić na wartość null.

```
LONG Close() throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, zwraca ERROR_SUCCESS; w przeciwnym razie zwraca wartość błędu.

##  <a name="create"></a>CRegKey:: Create

Wywołaj tę metodę, aby utworzyć określony klucz, jeśli nie istnieje jako podklucz elementu *hKeyParent*.

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

*hKeyParent*<br/>
Dojście otwartego klucza.

*lpszKeyName*<br/>
Określa nazwę klucza, który ma zostać utworzony lub otwarty. Ta nazwa musi być podkluczem *hKeyParent*.

*lpszClass*<br/>
Określa klasę klucza, który ma zostać utworzony lub otwarty. Wartość domyślna to REG_NONE.

*dwOptions*<br/>
Opcje klucza. Wartość domyślna to REG_OPTION_NON_VOLATILE. Aby uzyskać listę możliwych wartości i opisów, zobacz [RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) w Windows SDK.

*samDesired*<br/>
Dostęp zabezpieczeń dla klucza. Wartość domyślna to KEY_READ &#124; KEY_WRITE. Aby uzyskać listę możliwych wartości i opisów, zobacz `RegCreateKeyEx`.

*lpSecAttr*<br/>
Wskaźnik do struktury [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , który wskazuje, czy dojście klucza może być dziedziczone przez proces podrzędny. Domyślnie ten parametr ma wartość NULL (oznacza to, że dojście nie może być dziedziczone).

*lpdwDisposition*<br/>
określoną Jeśli wartość nie jest równa NULL, pobiera albo REG_CREATED_NEW_KEY (Jeśli klucz nie istnieje i został utworzony) lub REG_OPENED_EXISTING_KEY (Jeśli klucz istniał i został otwarty).

### <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, zwraca ERROR_SUCCESS i otwiera klucz. Jeśli metoda zakończy się niepowodzeniem, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w WINERROR. C.

### <a name="remarks"></a>Uwagi

`Create`Ustawia element członkowski [m_hKey](#m_hkey) na dojście tego klucza.

##  <a name="cregkey"></a>CRegKey:: CRegKey

Konstruktor.

```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Odwołanie do `CRegKey` obiektu.

*hKey*<br/>
Dojście do klucza rejestru.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

Tworzy nowy `CRegKey` obiekt. Obiekt można utworzyć na podstawie istniejącego `CRegKey` obiektu lub z dojścia do klucza rejestru.

##  <a name="dtor"></a>CRegKey:: ~ CRegKey

Destruktor.

```
~CRegKey() throw();
```

### <a name="remarks"></a>Uwagi

Destruktory są zwalniane `m_hKey`.

##  <a name="deletesubkey"></a>CRegKey::D eleteSubKey

Wywołaj tę metodę, aby usunąć określony klucz z rejestru.

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>Parametry

*lpszSubKey*<br/>
Określa nazwę klucza do usunięcia. Ta nazwa musi być podkluczem [m_hKey](#m_hkey).

### <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, zwraca ERROR_SUCCESS. Jeśli metoda zakończy się niepowodzeniem, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w WINERROR. C.

### <a name="remarks"></a>Uwagi

`DeleteSubKey`można usunąć tylko klucz, który nie ma podkluczy. Jeśli klucz ma podkluczy, wywołaj [RecurseDeleteKey](#recursedeletekey) zamiast.

##  <a name="deletevalue"></a>CRegKey::D eleteValue

Wywołaj tę metodę, aby usunąć pole wartości z [m_hKey](#m_hkey).

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>Parametry

*lpszValue*<br/>
Określa pole wartości do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, zwraca ERROR_SUCCESS. Jeśli metoda zakończy się niepowodzeniem, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w WINERROR. C.

##  <a name="detach"></a>CRegKey::D etach

Wywołaj tę metodę, aby [](#m_hkey) odłączyć uchwyt składowej m_hKey `CRegKey` z obiektu i `m_hKey` ustawić na wartość null.

```
HKEY Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

HKEY skojarzony z `CRegKey` obiektem.

##  <a name="enumkey"></a>CRegKey:: EnumKey

Wywołaj tę metodę, aby wyliczyć podklucze otwartego klucza rejestru.

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Indeks podklucza. Ten parametr powinien mieć wartość zero dla pierwszego wywołania, a następnie zwiększany w przypadku kolejnych wywołań

*pszName*<br/>
Wskaźnik do buforu, który odbiera nazwę podklucza, łącznie z kończącym znakiem null. Tylko nazwa podklucza jest kopiowana do bufora, a nie pełna hierarchia kluczy.

*pnNameLength*<br/>
Wskaźnik do zmiennej, która określa rozmiar, w TCHARs, buforu określonego przez parametr *pszName* . Ten rozmiar powinien zawierać kończący się znak null. Gdy metoda zwraca, zmienna wskazywana przez *pnNameLength* zawiera liczbę znaków przechowywanych w buforze. Zwracana liczba nie zawiera kończącego znaku null.

*pftLastWriteTime*<br/>
Wskaźnik do zmiennej, która odbiera czas ostatniego zapisu wyliczeniowego podklucza.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, wartość zwracana to ERROR_SUCCESS. Jeśli metoda zakończy się niepowodzeniem, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w WINERROR. C.

### <a name="remarks"></a>Uwagi

Aby wyliczyć podklucze, `CRegKey::EnumKey` Wywołaj z indeksem równym zero. Zwiększ wartość indeksu i powtórz operację do momentu, aż Metoda zwróci wartość ERROR_NO_MORE_ITEMS. Aby uzyskać więcej informacji, zobacz [RegEnumKeyEx](/windows/desktop/api/winreg/nf-winreg-regenumkeyexa) w Windows SDK.

##  <a name="flush"></a>CRegKey:: Flush

Wywołaj tę metodę, aby zapisać wszystkie atrybuty otwartego klucza rejestru w rejestrze.

```
LONG Flush() throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, wartość zwracana to ERROR_SUCCESS. Jeśli metoda zakończy się niepowodzeniem, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w WINERROR. C.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [RegEnumFlush](/windows/desktop/api/winreg/nf-winreg-regflushkey) w Windows SDK.

##  <a name="getkeysecurity"></a>CRegKey:: GetKeySecurity

Wywołaj tę metodę, aby pobrać kopię deskryptora zabezpieczeń chroniącą otwarty klucz rejestru.

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>Parametry

*si*<br/>
Wartość [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) , która wskazuje żądane informacje zabezpieczające.

*formacie*<br/>
Wskaźnik do buforu, który otrzymuje kopię żądanego deskryptora zabezpieczeń.

*pnBytes*<br/>
Rozmiar buforu wskazywanego przez *PSD*w bajtach.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, wartość zwracana to ERROR_SUCCESS. Jeśli metoda zakończy się niepowodzeniem, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w WINERROR. C.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [RegGetKeySecurity](/windows/desktop/api/winreg/nf-winreg-reggetkeysecurity).

##  <a name="m_hkey"></a>CRegKey:: m_hKey

Zawiera dojście klucza rejestru skojarzonego z `CRegKey` obiektem.

```
HKEY m_hKey;
```

##  <a name="m_ptm"></a>CRegKey:: m_pTM

Wskaźnik do `CAtlTransactionManager` obiektu.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Uwagi

##  <a name="notifychangekeyvalue"></a>CRegKey:: NotifyChangeKeyValue

Ta metoda powiadamia obiekt wywołujący o zmianach atrybutów lub zawartości otwartego klucza rejestru.

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bWatchSubtree*<br/>
Określa flagę wskazującą, czy należy zgłosić zmiany w określonym kluczu i wszystkich jego podkluczach lub tylko w określonym kluczu. Jeśli ten parametr ma wartość TRUE, metoda zgłasza zmiany w kluczu i jego podkluczach. Jeśli parametr ma wartość FALSE, Metoda raportuje zmiany tylko w kluczu.

*dwNotifyFilter*<br/>
Określa zestaw flag kontrolujących, które zmiany powinny być zgłaszane. Ten parametr może być kombinacją następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|Powiadom obiekt wywołujący, Jeśli podklucz zostanie dodany lub usunięty.|
|REG_NOTIFY_CHANGE_ATTRIBUTES|Powiadom obiekt wywołujący o zmianach atrybutów klucza, takich jak informacje deskryptora zabezpieczeń.|
|REG_NOTIFY_CHANGE_LAST_SET|Powiadom obiekt wywołujący o zmianach w wartości klucza. Może to obejmować dodanie lub usunięcie wartości lub zmianę istniejącej wartości.|
|REG_NOTIFY_CHANGE_SECURITY|Powiadom wywołującego o zmianach deskryptora zabezpieczeń klucza.|

*hEvent*<br/>
Dojście do zdarzenia. Jeśli parametr *bAsync* ma wartość true, metoda zwraca natychmiast, a zmiany są raportowane przez sygnalizowanie tego zdarzenia. Jeśli *bAsync* ma wartość false, *hevent* jest ignorowany.

*bAsync*<br/>
Określa flagę wskazującą, w jaki sposób Metoda zgłasza zmiany. Jeśli ten parametr ma wartość TRUE, Metoda wraca natychmiast i raportuje zmiany przez sygnalizowanie określonego zdarzenia. Jeśli ten parametr ma wartość FALSE, metoda nie zwraca, dopóki nie nastąpi zmiana. Jeśli *hevent* nie określa prawidłowego zdarzenia, parametr *bAsync* nie może mieć wartości true.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, wartość zwracana to ERROR_SUCCESS. Jeśli metoda zakończy się niepowodzeniem, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w WINERROR. C.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Ta metoda nie powiadamia obiektu wywołującego o usunięciu określonego klucza.

Aby uzyskać więcej szczegółów i przykładowego programu, zobacz [RegNotifyChangeKeyValue](/windows/desktop/api/winreg/nf-winreg-regnotifychangekeyvalue).

##  <a name="open"></a>CRegKey:: Open

Wywołaj tę metodę, aby otworzyć określony klucz i ustawić [m_hKey](#m_hkey) na dojście tego klucza.

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>Parametry

*hKeyParent*<br/>
Dojście otwartego klucza.

*lpszKeyName*<br/>
Określa nazwę klucza, który ma zostać utworzony lub otwarty. Ta nazwa musi być podkluczem *hKeyParent*.

*samDesired*<br/>
Dostęp zabezpieczeń dla klucza. Wartość domyślna to KEY_ALL_ACCESS. Aby uzyskać listę możliwych wartości i opisów, zobacz [RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, zwraca ERROR_SUCCESS; w przeciwnym razie wartość błędu różna od zera zdefiniowana w WINERROR. C.

### <a name="remarks"></a>Uwagi

Jeśli parametr *lpszKeyName* ma wartość null lub wskazuje na pusty ciąg, `Open` otwiera nowe dojście klucza identyfikowane przez *hKeyParent*, ale nie zamyka żadnego poprzednio otwartego dojścia.

W przeciwieństwie do [CRegKey:: Create](#create), nie utworzy określonego klucza, `Open` Jeśli nie istnieje.

##  <a name="operator_hkey"></a>CRegKey:: operator HKEY

`CRegKey` Konwertuje obiekt na HKEY.

```
operator HKEY() const throw();
```

##  <a name="operator_eq"></a>CRegKey:: operator =

Operator przypisania.

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do nowego klucza.

### <a name="remarks"></a>Uwagi

Ten operator odłącza *klucz* od jego bieżącego obiektu i przypisuje go do `CRegKey` obiektu.

##  <a name="querybinaryvalue"></a>CRegKey:: QueryBinaryValue

Wywołaj tę metodę, aby pobrać dane binarne dla określonej nazwy wartości.

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik na ciąg zakończony znakiem null zawierający nazwę wartości do zapytania.

*pValue*<br/>
Wskaźnik do buforu, który odbiera dane wartości.

*pnBytes*<br/>
Wskaźnik do zmiennej, która określa rozmiar (w bajtach) buforu wskazywanego przez parametr *pValue* . Gdy metoda zwraca, ta zmienna zawiera rozmiar danych skopiowanych do buforu.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, zostanie zwrócona wartość ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca kod błędu różny od zera zdefiniowany w WINERROR. C. Jeśli odwołanie do danych nie jest typu REG_BINARY, zwracany jest ERROR_INVALID_DATA.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta z programu `RegQueryValueEx` i potwierdza, że zwracany jest poprawny typ danych. Aby uzyskać więcej informacji, zobacz [działanie funkcji RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) .

> [!IMPORTANT]
>  Ta metoda umożliwia obiektowi wywołującemu określenie dowolnej lokalizacji w rejestrze, co potencjalnie może odczytywać dane, które nie są zaufane. Ponadto funkcja [działanie funkcji RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone wartością null. Kod wywołujący musi być sprawdzony dla obu warunków.

##  <a name="querydwordvalue"></a>CRegKey:: QueryDWORDValue

Wywołaj tę metodę, aby pobrać dane DWORD dla określonej nazwy wartości.

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik na ciąg zakończony znakiem null zawierający nazwę wartości do zapytania.

*dwValue*<br/>
Wskaźnik do buforu, który odbiera dane typu DWORD.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, zostanie zwrócona wartość ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca kod błędu różny od zera zdefiniowany w WINERROR. C. Jeśli przywoływane dane nie są typu REG_DWORD, zwracany jest ERROR_INVALID_DATA.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta z programu `RegQueryValueEx` i potwierdza, że zwracany jest poprawny typ danych. Aby uzyskać więcej informacji, zobacz [działanie funkcji RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) .

> [!IMPORTANT]
>  Ta metoda umożliwia obiektowi wywołującemu określenie dowolnej lokalizacji w rejestrze, co potencjalnie może odczytywać dane, które nie są zaufane. Ponadto funkcja [działanie funkcji RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone wartością null. Kod wywołujący musi być sprawdzony dla obu warunków.

##  <a name="queryguidvalue"></a>CRegKey:: QueryGUIDValue

Wywołaj tę metodę, aby pobrać dane identyfikatora GUID dla określonej nazwy wartości.

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik na ciąg zakończony znakiem null zawierający nazwę wartości do zapytania.

*guidValue*<br/>
Wskaźnik do zmiennej, która otrzymuje identyfikator GUID.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, zostanie zwrócona wartość ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca kod błędu różny od zera zdefiniowany w WINERROR. C. Jeśli dane, których dotyczy odwołanie, nie jest prawidłowym identyfikatorem GUID, zwracany jest ERROR_INVALID_DATA.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta z `CRegKey::QueryStringValue` i konwertuje ciąg na identyfikator GUID przy użyciu [CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring).

> [!IMPORTANT]
>  Ta metoda umożliwia obiektowi wywołującemu określenie dowolnej lokalizacji w rejestrze, co potencjalnie może odczytywać dane, które nie są zaufane.

##  <a name="querymultistringvalue"></a>CRegKey:: QueryMultiStringValue

Wywołaj tę metodę, aby pobrać dane z wielociągu dla określonej nazwy wartości.

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik na ciąg zakończony znakiem null zawierający nazwę wartości do zapytania.

*pszValue*<br/>
Wskaźnik do buforu, który odbiera dane wielociągowe. Wielociąg jest tablicą ciągów zakończonych wartością null, zakończonych przez dwa znaki null.

*pnChars*<br/>
Rozmiar buforu wskazywany przez *pszValue*w TCHARs. Gdy metoda zwraca, *pnChars* zawiera rozmiar, w TCHARs, pobierane z wielociągu, łącznie z kończącym znakiem null.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, zostanie zwrócona wartość ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca kod błędu różny od zera zdefiniowany w WINERROR. C. Jeśli dane, których dotyczy odwołanie, nie jest typu REG_MULTI_SZ, zwracany jest ERROR_INVALID_DATA.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta z programu `RegQueryValueEx` i potwierdza, że zwracany jest poprawny typ danych. Aby uzyskać więcej informacji, zobacz [działanie funkcji RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) .

> [!IMPORTANT]
>  Ta metoda umożliwia obiektowi wywołującemu określenie dowolnej lokalizacji w rejestrze, co potencjalnie może odczytywać dane, które nie są zaufane. Ponadto funkcja [działanie funkcji RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone wartością null. Kod wywołujący musi być sprawdzony dla obu warunków.

##  <a name="queryqwordvalue"></a>CRegKey:: QueryQWORDValue

Wywołaj tę metodę, aby pobrać dane QWORD dla określonej nazwy wartości.

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik na ciąg zakończony znakiem null zawierający nazwę wartości do zapytania.

*qwValue*<br/>
Wskaźnik do buforu, który odbiera wartość QWORD.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, zostanie zwrócona wartość ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca kod błędu różny od zera zdefiniowany w WINERROR. C. Jeśli przywoływane dane nie są typu REG_QWORD, zwracany jest ERROR_INVALID_DATA.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta z programu `RegQueryValueEx` i potwierdza, że zwracany jest poprawny typ danych. Aby uzyskać więcej informacji, zobacz [działanie funkcji RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) .

> [!IMPORTANT]
>  Ta metoda umożliwia obiektowi wywołującemu określenie dowolnej lokalizacji w rejestrze, co potencjalnie może odczytywać dane, które nie są zaufane. Ponadto funkcja [działanie funkcji RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone wartością null. Kod wywołujący musi być sprawdzony dla obu warunków.

##  <a name="querystringvalue"></a>CRegKey:: QueryStringValue

Wywołaj tę metodę, aby pobrać dane ciągu dla określonej nazwy wartości.

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik na ciąg zakończony znakiem null zawierający nazwę wartości do zapytania.

*pszValue*<br/>
Wskaźnik do buforu, który odbiera dane ciągu.

*pnChars*<br/>
Rozmiar buforu wskazywany przez *pszValue*w TCHARs. Gdy metoda zwraca, *pnChars* zawiera rozmiar, w TCHARs, pobranego ciągu, łącznie z kończącym znakiem null.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, zostanie zwrócona wartość ERROR_SUCCESS. Jeśli metoda nie może odczytać wartości, zwraca kod błędu różny od zera zdefiniowany w WINERROR. C. Jeśli dane, których dotyczy odwołanie, nie jest typu REG_SZ, zwracany jest ERROR_INVALID_DATA. Jeśli metoda zwraca ERROR_MORE_DATA, *pnChars* ma wartość zero, a nie wymagany rozmiar buforu w bajtach.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta z programu `RegQueryValueEx` i potwierdza, że zwracany jest poprawny typ danych. Aby uzyskać więcej informacji, zobacz [działanie funkcji RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) .

> [!IMPORTANT]
>  Ta metoda umożliwia obiektowi wywołującemu określenie dowolnej lokalizacji w rejestrze, co potencjalnie może odczytywać dane, które nie są zaufane. Ponadto funkcja [działanie funkcji RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone wartością null. Kod wywołujący musi być sprawdzony dla obu warunków.

##  <a name="queryvalue"></a>CRegKey:: QueryValue

Wywołaj tę metodę, aby pobrać dane dla określonego pola wartości [m_hKey](#m_hkey). Wcześniejsze wersje tej metody nie są już obsługiwane i są oznaczone jako ATL_DEPRECATED.

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

*pszValueName*<br/>
Wskaźnik na ciąg zakończony znakiem null zawierający nazwę wartości do zapytania. Jeśli *pszValueName* ma wartość null lub jest pustym ciągiem "", Metoda pobiera typ i dane dla nienazwy lub wartości domyślnej klucza, jeśli istnieje.

*pdwType*<br/>
Wskaźnik do zmiennej, która otrzymuje kod wskazujący typ danych przechowywanych w określonej wartości. Parametr *pdwType* może mieć wartość null, jeśli kod typu nie jest wymagany.

*pData*<br/>
Wskaźnik do buforu, który odbiera dane wartości. Ten parametr może mieć wartość NULL, jeśli dane nie są wymagane.

*pnBytes*<br/>
Wskaźnik do zmiennej, która określa rozmiar (w bajtach) buforu wskazywanego przez parametr *pData* . Gdy metoda zwraca, ta zmienna zawiera rozmiar danych skopiowanych do *pdata.*

*dwValue*<br/>
Dane liczbowe pola wartości.

*lpszValueName*<br/>
Określa pole wartości, którego ma dotyczyć zapytanie.

*szValue*<br/>
Dane ciągu wartości pola.

*pdwCount*<br/>
Rozmiar danych ciągu. Wartość jest początkowo ustawiona na rozmiar buforu *szValue* .

### <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, zwraca ERROR_SUCCESS; w przeciwnym razie kod błędu różny od zera zdefiniowany w WINERROR. C.

### <a name="remarks"></a>Uwagi

Dwie wersje `QueryValue` pierwotne nie są już obsługiwane i są oznaczone jako ATL_DEPRECATED. Kompilator wyświetli ostrzeżenie, jeśli są używane te formularze.

Pozostałe metody wywołania działanie funkcji RegQueryValueEx.

> [!IMPORTANT]
>  Ta metoda umożliwia obiektowi wywołującemu określenie dowolnej lokalizacji w rejestrze, co potencjalnie może odczytywać dane, które nie są zaufane. Ponadto funkcja działanie funkcji RegQueryValueEx używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone wartością NULL. Kod wywołujący musi być sprawdzony dla obu warunków.

##  <a name="recursedeletekey"></a>CRegKey:: RecurseDeleteKey

Wywołaj tę metodę, aby usunąć określony klucz z rejestru i jawnie usunąć wszystkie podklucze.

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>Parametry

*lpszKey*<br/>
Określa nazwę klucza do usunięcia. Ta nazwa musi być podkluczem [m_hKey](#m_hkey).

### <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, zwraca ERROR_SUCCESS; w przeciwnym razie wartość błędu różna od zera zdefiniowana w WINERROR. C.

### <a name="remarks"></a>Uwagi

Jeśli klucz ma podklucze, należy wywołać tę metodę, aby usunąć klucz.

##  <a name="setbinaryvalue"></a>CRegKey:: SetBinaryValue

Wywołaj tę metodę, aby ustawić wartość binarną klucza rejestru.

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik na ciąg zawierający nazwę wartości do ustawienia. Jeśli wartość o tej nazwie jeszcze nie istnieje, Metoda dodaje ją do klucza.

*pValue*<br/>
Wskaźnik do buforu zawierającego dane, które mają być przechowywane z określoną nazwą wartości.

*nBytes*<br/>
Określa rozmiar w bajtach informacji wskazywanych przez parametr *pValue* .

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, wartość zwracana to ERROR_SUCCESS. Jeśli metoda zakończy się niepowodzeniem, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w WINERROR. C.

### <a name="remarks"></a>Uwagi

Ta metoda używa [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) do zapisania wartości w rejestrze.

##  <a name="setdwordvalue"></a>CRegKey:: SetDWORDValue

Wywołaj tę metodę, aby ustawić wartość DWORD klucza rejestru.

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik na ciąg zawierający nazwę wartości do ustawienia. Jeśli wartość o tej nazwie jeszcze nie istnieje, Metoda dodaje ją do klucza.

*dwValue*<br/>
Dane DWORD, które mają być przechowywane z określoną nazwą wartości.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, wartość zwracana to ERROR_SUCCESS. Jeśli metoda zakończy się niepowodzeniem, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w WINERROR. C.

### <a name="remarks"></a>Uwagi

Ta metoda używa [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) do zapisania wartości w rejestrze.

##  <a name="setguidvalue"></a>CRegKey:: SetGUIDValue

Wywołaj tę metodę, aby ustawić wartość identyfikatora GUID klucza rejestru.

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik na ciąg zawierający nazwę wartości do ustawienia. Jeśli wartość o tej nazwie jeszcze nie istnieje, Metoda dodaje ją do klucza.

*guidValue*<br/>
Odwołanie do identyfikatora GUID, który ma być przechowywany przy użyciu określonej nazwy wartości.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, wartość zwracana to ERROR_SUCCESS. Jeśli metoda zakończy się niepowodzeniem, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w WINERROR. C.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta z `CRegKey::SetStringValue` i konwertuje identyfikator GUID na ciąg za pomocą [StringFromGUID2](/windows/desktop/api/combaseapi/nf-combaseapi-stringfromguid2).

##  <a name="setkeyvalue"></a>CRegKey:: SetKeyValue

Wywołaj tę metodę, aby przechowywać dane w określonym polu wartości określonego klucza.

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>Parametry

*lpszKeyName*<br/>
Określa nazwę klucza, który ma zostać utworzony lub otwarty. Ta nazwa musi być podkluczem [m_hKey](#m_hkey).

*lpszValue*<br/>
Określa dane, które mają być przechowywane. Ten parametr nie może mieć wartości NULL.

*lpszValueName*<br/>
Określa pole wartości, które ma zostać ustawione. Jeśli pole wartości o tej nazwie nie istnieje jeszcze w kluczu, zostanie dodane.

### <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, zwraca ERROR_SUCCESS; w przeciwnym razie kod błędu różny od zera zdefiniowany w WINERROR. C.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby utworzyć lub otworzyć klucz *lpszKeyName* i zapisać dane *lpszValue* w polu wartość *lpszValueName* .

##  <a name="setkeysecurity"></a>CRegKey:: SetKeySecurity

Wywołaj tę metodę, aby ustawić zabezpieczenia klucza rejestru.

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>Parametry

*si*<br/>
Określa składniki deskryptora zabezpieczeń, które mają zostać ustawione. Wartość może być kombinacją następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|Ustawia poufną listę kontroli dostępu (DACL) klucza. Klucz musi mieć dostęp WRITE_DAC lub proces wywołujący musi być właścicielem obiektu.|
|GROUP_SECURITY_INFORMATION|Ustawia podstawowy identyfikator zabezpieczeń (SID) klucza. Klucz musi mieć dostęp WRITE_OWNER lub proces wywołujący musi być właścicielem obiektu.|
|OWNER_SECURITY_INFORMATION|Ustawia identyfikator SID właściciela klucza. Klucz musi mieć dostęp WRITE_OWNER lub proces wywołujący musi być właścicielem obiektu lub mieć włączone uprawnienie SE_TAKE_OWNERSHIP_NAME.|
|SACL_SECURITY_INFORMATION|Ustawia listę kontroli dostępu do systemu (SACL) klucza. Klucz musi mieć dostęp ACCESS_SYSTEM_SECURITY. Odpowiednim sposobem uzyskania dostępu jest włączenie [uprawnienia](/windows/desktop/secauthz/privileges) SE_SECURITY_NAME w bieżącym tokenie dostępu obiektu wywołującego, otwarcie dojścia do ACCESS_SYSTEM_SECURITY Access, a następnie wyłączenie tego uprawnienia.|

*formacie*<br/>
Wskaźnik na strukturę [SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-security_descriptor) , która określa atrybuty zabezpieczeń, które mają zostać ustawione dla określonego klucza.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, wartość zwracana to ERROR_SUCCESS. Jeśli metoda zakończy się niepowodzeniem, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w WINERROR. C.

### <a name="remarks"></a>Uwagi

Ustawia atrybuty zabezpieczeń klucza. Aby uzyskać więcej informacji, zobacz [RegSetKeySecurity](/windows/desktop/api/winreg/nf-winreg-regsetkeysecurity) .

##  <a name="setmultistringvalue"></a>CRegKey:: SetMultiStringValue

Wywołaj tę metodę, aby ustawić wartość wielociągową klucza rejestru.

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik na ciąg zawierający nazwę wartości do ustawienia. Jeśli wartość o tej nazwie jeszcze nie istnieje, Metoda dodaje ją do klucza.

*pszValue*<br/>
Wskaźnik do danych wielociągowych, które mają być przechowywane z określoną nazwą wartości. Wielociąg jest tablicą ciągów zakończonych wartością null, zakończonych przez dwa znaki null.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, wartość zwracana to ERROR_SUCCESS. Jeśli metoda zakończy się niepowodzeniem, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w WINERROR. C.

### <a name="remarks"></a>Uwagi

Ta metoda używa [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) do zapisania wartości w rejestrze.

##  <a name="setqwordvalue"></a>CRegKey:: SetQWORDValue

Wywołaj tę metodę, aby ustawić wartość QWORD klucza rejestru.

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik na ciąg zawierający nazwę wartości do ustawienia. Jeśli wartość o tej nazwie jeszcze nie istnieje, Metoda dodaje ją do klucza.

*qwValue*<br/>
Dane QWORD, które mają być przechowywane z określoną nazwą wartości.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, wartość zwracana to ERROR_SUCCESS. Jeśli metoda zakończy się niepowodzeniem, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w WINERROR. C.

### <a name="remarks"></a>Uwagi

Ta metoda używa [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) do zapisania wartości w rejestrze.

##  <a name="setstringvalue"></a>CRegKey:: SetStringValue

Wywołaj tę metodę, aby ustawić wartość ciągu klucza rejestru.

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik na ciąg zawierający nazwę wartości do ustawienia. Jeśli wartość o tej nazwie jeszcze nie istnieje, Metoda dodaje ją do klucza.

*pszValue*<br/>
Wskaźnik na dane ciągu, który ma być przechowywany przy użyciu określonej nazwy wartości.

*dwType*<br/>
Typ ciągu do zapisu w rejestrze: REG_SZ (wartość domyślna) lub REG_EXPAND_SZ (dla wielociągów).

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda zakończy się pomyślnie, wartość zwracana to ERROR_SUCCESS. Jeśli metoda zakończy się niepowodzeniem, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w WINERROR. C.

### <a name="remarks"></a>Uwagi

Ta metoda używa [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) do zapisania wartości w rejestrze.

##  <a name="setvalue"></a>CRegKey:: SetValue

Wywołaj tę metodę, aby przechowywać dane w określonym polu wartości [m_hKey](#m_hkey). Wcześniejsze wersje tej metody nie są już obsługiwane i są oznaczone jako ATL_DEPRECATED.

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

*pszValueName*<br/>
Wskaźnik na ciąg zawierający nazwę wartości do ustawienia. Jeśli wartość o tej nazwie nie jest już obecna w kluczu, Metoda dodaje ją do klucza. Jeśli *pszValueName* ma wartość null lub jest pustym ciągiem "", Metoda ustawia typ i dane dla nienazwanego lub wartości domyślnej klucza.

*dwType*<br/>
Określa kod wskazujący typ danych wskazywanych przez parametr *pValue* .

*pValue*<br/>
Wskaźnik do buforu zawierającego dane, które mają być przechowywane z określoną nazwą wartości.

*nBytes*<br/>
Określa rozmiar w bajtach informacji wskazywanych przez parametr *pValue* . Jeśli dane są typu REG_SZ, REG_EXPAND_SZ lub REG_MULTI_SZ, *nBytes* musi zawierać rozmiar kończącego znaku null.

*hKeyParent*<br/>
Dojście otwartego klucza.

*lpszKeyName*<br/>
Określa nazwę klucza, który ma zostać utworzony lub otwarty. Ta nazwa musi być podkluczem *hKeyParent*.

*lpszValue*<br/>
Określa dane, które mają być przechowywane. Ten parametr nie może mieć wartości NULL.

*lpszValueName*<br/>
Określa pole wartości, które ma zostać ustawione. Jeśli pole wartości o tej nazwie nie istnieje jeszcze w kluczu, zostanie dodane.

*dwValue*<br/>
Określa dane, które mają być przechowywane.

*bMulti*<br/>
W przypadku wartości false wskazuje, że ciąg jest typu REG_SZ. Jeśli ma wartość true, wskazuje, że ciąg jest wielociągowym typem REG_MULTI_SZ.

*nValueLen*<br/>
Jeśli *bMulti* ma wartość true, *nValueLen* jest długości ciągu *lpszValue* w znakach. Jeśli *bMulti* ma wartość false, wartość-1 wskazuje, że metoda automatycznie obliczy długość.

### <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, zwraca ERROR_SUCCESS; w przeciwnym razie kod błędu różny od zera zdefiniowany w WINERROR. C.

### <a name="remarks"></a>Uwagi

Dwie oryginalne wersje programu `SetValue` są oznaczone jako ATL_DEPRECATED i nie powinny być już używane. Kompilator wyświetli ostrzeżenie, jeśli są używane te formularze.

Trzecia metoda wywołuje [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa).

## <a name="see-also"></a>Zobacz także

[Przykład DCOM](../../overview/visual-cpp-samples.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
