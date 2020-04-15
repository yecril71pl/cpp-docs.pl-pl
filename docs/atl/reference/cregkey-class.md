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
ms.openlocfilehash: 01810c16ff3e7fbc930983b9a52dc3a80f779f14
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331038"
---
# <a name="cregkey-class"></a>Klasa CRegKey

Ta klasa zawiera metody manipulowania wpisami w rejestrze systemowym.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CRegKey
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRegKey::CRegKey](#cregkey)|Konstruktor.|
|[CRegKey::~CRegKey](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRegKey::Dołącz](#attach)|Wywołanie tej metody, aby `CRegKey` dołączyć HKEY do obiektu, ustawiając [m_hKey](#m_hkey) dojścia elementu członkowskiego do `hKey`.|
|[CRegKey::Zamknij](#close)|Wywołanie tej metody, aby zwolnić [dojście elementu](#m_hkey) członkowskiego m_hKey i ustawić go na NULL.|
|[CRegKey::Utwórz](#create)|Wywołanie tej metody, aby utworzyć określony klucz, jeśli `hKeyParent`nie istnieje jako podklucz .|
|[CRegKey::DeleteSubKey](#deletesubkey)|Wywołanie tej metody, aby usunąć określony klucz z rejestru.|
|[CRegKey::DeleteValue](#deletevalue)|Wywołanie tej metody, aby usunąć pole wartości z [m_hKey](#m_hkey).|
|[CRegKey::Detach](#detach)|Wywołanie tej metody, [m_hKey](#m_hkey) aby odłączyć `CRegKey` m_hKey dojście elementu członkowskiego od obiektu i ustawić `m_hKey` wartość NULL.|
|[CRegKey::WyliczeniaNak](#enumkey)|Wywołanie tej metody, aby wyliczyć podkluczy klucza otwartego rejestru.|
|[CRegKey::Opróżnij](#flush)|Wywołanie tej metody, aby zapisać wszystkie atrybuty otwartego klucza rejestru w rejestrze.|
|[CRegKey::GetKeySecurity](#getkeysecurity)|Wywołanie tej metody, aby pobrać kopię deskryptora zabezpieczeń chroniące otwarty klucz rejestru.|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|Ta metoda powiadamia wywołującego o zmianach atrybutów lub zawartości otwartego klucza rejestru.|
|[CRegKey::Otwórz](#open)|Wywołanie tej metody, aby otworzyć określony klucz i ustawić [m_hKey](#m_hkey) do dojścia tego klucza.|
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|Wywołanie tej metody, aby pobrać dane binarne dla określonej nazwy wartości.|
|[CRegKey::QueryDWORDValue](#querydwordvalue)|Wywołanie tej metody, aby pobrać dane DWORD dla określonej nazwy wartości.|
|[CRegKey::QueryGUIDValue](#queryguidvalue)|Wywołanie tej metody, aby pobrać dane GUID dla określonej nazwy wartości.|
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|Wywołanie tej metody, aby pobrać dane wielociągowe dla określonej nazwy wartości.|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|Wywołanie tej metody, aby pobrać dane QWORD dla określonej nazwy wartości.|
|[CRegKey::QueryStringValue](#querystringvalue)|Wywołanie tej metody, aby pobrać dane ciągu dla określonej nazwy wartości.|
|[CRegKey::QueryValue](#queryvalue)|Wywołanie tej metody, aby pobrać dane dla określonego pola wartości [m_hKey](#m_hkey). Wcześniejsze wersje tej metody nie są już obsługiwane i są oznaczone jako ATL_DEPRECATED.|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|Wywołanie tej metody, aby usunąć określony klucz z rejestru i jawnie usunąć wszystkie podkluczy.|
|[CRegKey::SetBinaryValue](#setbinaryvalue)|Wywołanie tej metody, aby ustawić wartość binarną klucza rejestru.|
|[CRegKey::SetDWORDValue](#setdwordvalue)|Wywołanie tej metody, aby ustawić wartość DWORD klucza rejestru.|
|[CRegKey::SetGUIDValue](#setguidvalue)|Wywołanie tej metody, aby ustawić wartość GUID klucza rejestru.|
|[CRegKey::SetKeySecurity](#setkeysecurity)|Wywołanie tej metody, aby ustawić bezpieczeństwo klucza rejestru.|
|[CRegKey::SetKeyValue](#setkeyvalue)|Wywołanie tej metody do przechowywania danych w określonym polu wartości określonego klucza.|
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|Wywołanie tej metody, aby ustawić wartość wielociągową klucza rejestru.|
|[CRegKey::SetQWORDValue](#setqwordvalue)|Wywołanie tej metody, aby ustawić wartość QWORD klucza rejestru.|
|[CRegKey::SetStringValue](#setstringvalue)|Wywołanie tej metody, aby ustawić wartość ciągu klucza rejestru.|
|[CRegKey::SetValue](#setvalue)|Wywołanie tej metody do przechowywania danych w określonym polu wartości [m_hKey](#m_hkey). Wcześniejsze wersje tej metody nie są już obsługiwane i są oznaczone jako ATL_DEPRECATED.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRegKey::operator HKEY](#operator_hkey)|Konwertuje `CRegKey` obiekt na HKEY.|
|[CRegKey::operator =](#operator_eq)|Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|Zawiera dojście klucza rejestru `CRegKey` skojarzonego z obiektem.|
|[CRegKey::m_pTM](#m_ptm)|Wskaźnik `CAtlTransactionManager` do obiektu|

## <a name="remarks"></a>Uwagi

`CRegKey`udostępnia metody tworzenia i usuwania kluczy i wartości w rejestrze systemowym. Rejestr zawiera zestaw definicji specyficznych dla instalacji dla składników systemu, takich jak numery wersji oprogramowania, logiczne do fizyczne mapowania zainstalowanego sprzętu i obiekty COM.

`CRegKey`zapewnia interfejs programowania do rejestru systemu dla danego komputera. Na przykład, aby otworzyć określony `CRegKey::Open`klucz rejestru, zadzwoń . Aby pobrać lub zmodyfikować wartość `CRegKey::QueryValue` `CRegKey::SetValue`danych, wywołać lub , odpowiednio. Aby zamknąć klucz, zadzwoń do `CRegKey::Close`pliku .

Po zamknięciu klucza jego dane rejestru są zapisywane (opróżniane) na dysku twardym. Ten proces może potrwać kilka sekund. Jeśli aplikacja musi jawnie zapisywać dane rejestru na dysku twardym, można wywołać funkcję [RegFlushKey](/windows/win32/api/winreg/nf-winreg-regflushkey) Win32. Jednak `RegFlushKey` używa wielu zasobów systemowych i powinny być wywoływane tylko wtedy, gdy jest to absolutnie konieczne.

> [!IMPORTANT]
> Wszelkie metody, które umożliwiają wywołującemu określić lokalizację rejestru mają potencjał do odczytu danych, które nie mogą być zaufane. Metody, które korzystają z [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) należy wziąć pod uwagę, że ta funkcja nie jawnie obsługiwać ciągi, które są NULL zakończone. Oba warunki powinny być sprawdzane przez kod wywołujący.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="cregkeyattach"></a><a name="attach"></a>CRegKey::Dołącz

Wywołanie tej metody, aby `CRegKey` dołączyć HKEY do obiektu, ustawiając [m_hKey](#m_hkey) dojście elementu członkowskiego do *hKey*.

```
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>Parametry

*klawiszy*<br/>
Dojście klucza rejestru.

### <a name="remarks"></a>Uwagi

`Attach`potwierdzi, `m_hKey` jeśli nie jest null.

## <a name="cregkeyclose"></a><a name="close"></a>CRegKey::Zamknij

Wywołanie tej metody, aby zwolnić [dojście elementu](#m_hkey) członkowskiego m_hKey i ustawić go na NULL.

```
LONG Close() throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie zwraca wartość błędu.

## <a name="cregkeycreate"></a><a name="create"></a>CRegKey::Utwórz

Wywołanie tej metody, aby utworzyć określony klucz, jeśli nie istnieje jako podklucz *hKeyParent*.

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
Uchwyt otwartego klucza.

*lpszKeyName (Nazwa_*<br/>
Określa nazwę klucza, który ma zostać utworzony lub otwarty. Ta nazwa musi być podkluczem *hKeyParent*.

*lpszClass (klasa)*<br/>
Określa klasę klucza, który ma zostać utworzony lub otwarty. Wartość domyślna jest REG_NONE.

*Dwoptions*<br/>
Opcje klucza. Wartość domyślna to REG_OPTION_NON_VOLATILE. Aby uzyskać listę możliwych wartości i opisów, zobacz [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) w zestawie Windows SDK.

*samDesired (polski)*<br/>
Dostęp zabezpieczeń dla klucza. Wartość domyślna to KEY_READ &#124; KEY_WRITE. Aby uzyskać listę możliwych wartości i `RegCreateKeyEx`opisów, zobacz .

*lpSecAttr*<br/>
Wskaźnik do [struktury SECURITY_ATTRIBUTES,](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) który wskazuje, czy dojście klucza może być dziedziczone przez proces podrzędny. Domyślnie ten parametr ma wartość NULL (co oznacza, że uchwyt nie może być dziedziczony).

*lpdwDisposition*<br/>
[na zewnątrz] Jeśli wartość null, pobiera REG_CREATED_NEW_KEY (jeśli klucz nie istnieje i został utworzony) lub REG_OPENED_EXISTING_KEY (jeśli klucz istniał i został otwarty).

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca ERROR_SUCCESS i otwiera klucz. Jeśli metoda nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w WINERROR. H.

### <a name="remarks"></a>Uwagi

`Create`ustawia [element](#m_hkey) członkowski m_hKey do uchwytu tego klucza.

## <a name="cregkeycregkey"></a><a name="cregkey"></a>CRegKey::CRegKey

Konstruktor.

```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Odwołanie do `CRegKey` obiektu.

*klawiszy*<br/>
Dojście do klucza rejestru.

*Ptm*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

Tworzy nowy `CRegKey` obiekt. Obiekt można utworzyć z `CRegKey` istniejącego obiektu lub z dojścia do klucza rejestru.

## <a name="cregkeycregkey"></a><a name="dtor"></a>CRegKey::~CRegKey

Destruktor.

```
~CRegKey() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia `m_hKey`.

## <a name="cregkeydeletesubkey"></a><a name="deletesubkey"></a>CRegKey::DeleteSubKey

Wywołanie tej metody, aby usunąć określony klucz z rejestru.

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>Parametry

*lpszsubKey (klawisz)*<br/>
Określa nazwę klucza do usunięcia. Ta nazwa musi być podkluczem [m_hKey](#m_hkey).

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca ERROR_SUCCESS. Jeśli metoda nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w WINERROR. H.

### <a name="remarks"></a>Uwagi

`DeleteSubKey`można usunąć tylko klucz, który nie ma podkluczów. Jeśli klucz ma podklucze, [wywołanie RecurseDeleteKey](#recursedeletekey) zamiast.

## <a name="cregkeydeletevalue"></a><a name="deletevalue"></a>CRegKey::DeleteValue

Wywołanie tej metody, aby usunąć pole wartości z [m_hKey](#m_hkey).

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>Parametry

*lpszValue*<br/>
Określa pole wartości do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca ERROR_SUCCESS. Jeśli metoda nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w WINERROR. H.

## <a name="cregkeydetach"></a><a name="detach"></a>CRegKey::Detach

Wywołanie tej metody, [m_hKey](#m_hkey) aby odłączyć `CRegKey` m_hKey dojście elementu członkowskiego od obiektu i ustawić `m_hKey` wartość NULL.

```
HKEY Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Klucz HKEY skojarzony `CRegKey` z obiektem.

## <a name="cregkeyenumkey"></a><a name="enumkey"></a>CRegKey::WyliczeniaNak

Wywołanie tej metody, aby wyliczyć podkluczy klucza otwartego rejestru.

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
Indeks podklucza. Ten parametr powinien być zerowy dla pierwszego wywołania, a następnie zwiększany dla kolejnych wywołań

*pszName (Nazwa psz)*<br/>
Wskaźnik do buforu, który odbiera nazwę podklucza, w tym kończący się znak null. Tylko nazwa podklucza jest kopiowana do buforu, a nie do pełnej hierarchii kluczy.

*pnNameLength*<br/>
Wskaźnik do zmiennej, która określa rozmiar w CZAR buforu określonego przez *pszName* parametru. Ten rozmiar powinien zawierać kończący się znak null. Gdy metoda zwraca, zmienna wskazywalna przez *pnNameLength* zawiera liczbę znaków przechowywanych w buforze. Zwrócona liczba nie zawiera kończącego się znaku zerowego.

*pftLastWriteTime*<br/>
Wskaźnik do zmiennej, która odbiera czas wyliczonego podklucza został ostatnio napisany.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w WINERROR. H.

### <a name="remarks"></a>Uwagi

Aby wyliczyć podkluczy, wywołaj `CRegKey::EnumKey` z indeksem zero. Przyrost wartości indeksu i powtarzać, aż metoda zwraca ERROR_NO_MORE_ITEMS. Aby uzyskać więcej informacji, zobacz [RegEnumKeyEx](/windows/win32/api/winreg/nf-winreg-regenumkeyexw) w windows SDK.

## <a name="cregkeyflush"></a><a name="flush"></a>CRegKey::Opróżnij

Wywołanie tej metody, aby zapisać wszystkie atrybuty otwartego klucza rejestru w rejestrze.

```
LONG Flush() throw();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w WINERROR. H.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [RegEnumFlush](/windows/win32/api/winreg/nf-winreg-regflushkey) w windows SDK.

## <a name="cregkeygetkeysecurity"></a><a name="getkeysecurity"></a>CRegKey::GetKeySecurity

Wywołanie tej metody, aby pobrać kopię deskryptora zabezpieczeń chroniące otwarty klucz rejestru.

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>Parametry

*Si*<br/>
Wartość [SECURITY_INFORMATION,](/windows/win32/SecAuthZ/security-information) która wskazuje żądane informacje zabezpieczające.

*Psd*<br/>
Wskaźnik do buforu, który odbiera kopię żądanego deskryptora zabezpieczeń.

*PnBytes ( pnBytes )*<br/>
Rozmiar w bajtach buforu wskazanego przez *psd*.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, zwracana wartość jest kod błędu niezerowego jest zdefiniowany w WINERROR. H.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [RegGetKeySecurity](/windows/win32/api/winreg/nf-winreg-reggetkeysecurity).

## <a name="cregkeym_hkey"></a><a name="m_hkey"></a>CRegKey::m_hKey

Zawiera dojście klucza rejestru `CRegKey` skojarzonego z obiektem.

```
HKEY m_hKey;
```

## <a name="cregkeym_ptm"></a><a name="m_ptm"></a>CRegKey::m_pTM

Wskaźnik do `CAtlTransactionManager` obiektu.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Uwagi

## <a name="cregkeynotifychangekeyvalue"></a><a name="notifychangekeyvalue"></a>CRegKey::NotifyChangeKeyValue

Ta metoda powiadamia wywołującego o zmianach atrybutów lub zawartości otwartego klucza rejestru.

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bWatchSubtree*<br/>
Określa flagę, która wskazuje, czy mają być raportowane zmiany w określonym kluczu i wszystkich jego podkluczy lub tylko w określonym kluczu. Jeśli ten parametr ma wartość PRAWDA, metoda zgłasza zmiany w kluczu i jego podkluczach. Jeśli parametr jest FALSE, raportuje metodę zmienia się tylko w kluczu.

*dwNotifyFilter*<br/>
Określa zestaw flag, które kontrolują, które zmiany powinny być zgłaszane. Ten parametr może być kombinacją następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|Powiadom rozmówcę o dodaniu lub usunięciu podklucza.|
|REG_NOTIFY_CHANGE_ATTRIBUTES|Powiadamiaj rozmówcę o zmianach atrybutów klucza, takich jak informacje o deskryptorze zabezpieczeń.|
|REG_NOTIFY_CHANGE_LAST_SET|Powiadamiaj wywołującego o zmianach wartości klucza. Może to obejmować dodawanie lub usuwanie wartości lub zmianę istniejącej wartości.|
|REG_NOTIFY_CHANGE_SECURITY|Powiadamiaj rozmówcę o zmianach w deskryptorze zabezpieczeń klucza.|

*hWentowiny*<br/>
Dojście do zdarzenia. Jeśli parametr *bAsync* ma wartość PRAWDA, metoda zwraca natychmiast i zmiany są zgłaszane przez sygnalizowanie tego zdarzenia. Jeśli *bAsync* jest FALSE, *hEvent* jest ignorowany.

*bSync*<br/>
Określa flagę wskazującą, jak zmienia się metoda. Jeśli ten parametr ma wartość PRAWDA, metoda zwraca natychmiast i zgłasza zmiany, sygnalizując określone zdarzenie. Gdy ten parametr jest FALSE, metoda nie zwraca, dopóki nie nastąpiła zmiana. Jeśli *hEvent* nie określa prawidłowego zdarzenia, parametr *bAsync* nie może być true.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w WINERROR. H.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Ta metoda nie powiadamia wywołującego, jeśli określony klucz zostanie usunięty.

Aby uzyskać więcej informacji i przykładowy program, zobacz [RegNotifyChangeKeyValue](/windows/win32/api/winreg/nf-winreg-regnotifychangekeyvalue).

## <a name="cregkeyopen"></a><a name="open"></a>CRegKey::Otwórz

Wywołanie tej metody, aby otworzyć określony klucz i ustawić [m_hKey](#m_hkey) do dojścia tego klucza.

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>Parametry

*hKeyParent*<br/>
Uchwyt otwartego klucza.

*lpszKeyName (Nazwa_*<br/>
Określa nazwę klucza, który ma zostać utworzony lub otwarty. Ta nazwa musi być podkluczem *hKeyParent*.

*samDesired (polski)*<br/>
Dostęp zabezpieczeń dla klucza. Wartość domyślna jest KEY_ALL_ACCESS. Aby uzyskać listę możliwych wartości i opisów, zobacz [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie wartość błędu niezerowego zdefiniowana w WINERROR. H.

### <a name="remarks"></a>Uwagi

Jeśli parametr *lpszKeyName* ma wartość NULL lub `Open` wskazuje pusty ciąg, otwiera nowy uchwyt klucza identyfikowanego przez *hKeyParent*, ale nie zamyka żadnego wcześniej otwartego dojścia.

W przeciwieństwie do [CRegKey::Create](#create), `Open` nie utworzy określonego klucza, jeśli nie istnieje.

## <a name="cregkeyoperator-hkey"></a><a name="operator_hkey"></a>CRegKey::operator HKEY

Konwertuje `CRegKey` obiekt na HKEY.

```
operator HKEY() const throw();
```

## <a name="cregkeyoperator-"></a><a name="operator_eq"></a>CRegKey::operator =

Operator przypisania.

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do nowego klucza.

### <a name="remarks"></a>Uwagi

Ten operator odłącza *klucz* od bieżącego obiektu `CRegKey` i przypisuje go do obiektu.

## <a name="cregkeyquerybinaryvalue"></a><a name="querybinaryvalue"></a>CRegKey::QueryBinaryValue

Wywołanie tej metody, aby pobrać dane binarne dla określonej nazwy wartości.

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik do ciągu zakończonego wartością null zawierającego nazwę wartości do kwerendy.

*wartość pValue*<br/>
Wskaźnik do buforu, który odbiera dane wartości.

*PnBytes ( pnBytes )*<br/>
Wskaźnik do zmiennej, która określa rozmiar w bajtach buforu wskazywał przez parametr *pValue.* Gdy metoda zwraca, ta zmienna zawiera rozmiar danych skopiowanych do buforu.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, ERROR_SUCCESS jest zwracany. Jeśli metoda nie odczytuje wartości, zwraca kod błędu niezerowego zdefiniowany w WINERROR. H. Jeśli dane, do których się odwołuje, nie są REG_BINARY typu, zwracany jest ERROR_INVALID_DATA.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta `RegQueryValueEx` i potwierdza, że zwracany jest poprawny typ danych. Zobacz [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) aby uzyskać więcej informacji.

> [!IMPORTANT]
> Ta metoda umożliwia wywołującemu określić dowolną lokalizację rejestru, potencjalnie odczytywania danych, których nie można ufać. Ponadto [Funkcja RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone wartością NULL. Oba warunki powinny być sprawdzane przez kod wywołujący.

## <a name="cregkeyquerydwordvalue"></a><a name="querydwordvalue"></a>CRegKey::QueryDWORDValue

Wywołanie tej metody, aby pobrać dane DWORD dla określonej nazwy wartości.

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik do ciągu zakończonego wartością null zawierającego nazwę wartości do kwerendy.

*dwValue (Wartość dwValue)*<br/>
Wskaźnik do buforu, który odbiera DWORD.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, ERROR_SUCCESS jest zwracany. Jeśli metoda nie odczytuje wartości, zwraca kod błędu niezerowego zdefiniowany w WINERROR. H. Jeśli dane, do których się odwołuje, nie są REG_DWORD typu, zwracany jest ERROR_INVALID_DATA.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta `RegQueryValueEx` i potwierdza, że zwracany jest poprawny typ danych. Zobacz [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) aby uzyskać więcej informacji.

> [!IMPORTANT]
> Ta metoda umożliwia wywołującemu określić dowolną lokalizację rejestru, potencjalnie odczytywania danych, których nie można ufać. Ponadto [Funkcja RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone wartością NULL. Oba warunki powinny być sprawdzane przez kod wywołujący.

## <a name="cregkeyqueryguidvalue"></a><a name="queryguidvalue"></a>CRegKey::QueryGUIDValue

Wywołanie tej metody, aby pobrać dane GUID dla określonej nazwy wartości.

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik do ciągu zakończonego wartością null zawierającego nazwę wartości do kwerendy.

*wartość guidValue*<br/>
Wskaźnik do zmiennej odbiera ącej identyfikator GUID.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, ERROR_SUCCESS jest zwracany. Jeśli metoda nie odczytuje wartości, zwraca kod błędu niezerowego zdefiniowany w WINERROR. H. Jeśli dane, do których się odwołuje, nie są prawidłowym identyfikatorem GUID, zwracany jest ERROR_INVALID_DATA.

### <a name="remarks"></a>Uwagi

Ta metoda wykorzystuje `CRegKey::QueryStringValue` i konwertuje ciąg na identyfikator GUID przy użyciu [CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring).

> [!IMPORTANT]
> Ta metoda umożliwia wywołującemu określić dowolną lokalizację rejestru, potencjalnie odczytywania danych, których nie można ufać.

## <a name="cregkeyquerymultistringvalue"></a><a name="querymultistringvalue"></a>CRegKey::QueryMultiStringValue

Wywołanie tej metody, aby pobrać dane wielociągowe dla określonej nazwy wartości.

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik do ciągu zakończonego wartością null zawierającego nazwę wartości do kwerendy.

*pszValue (właskw.*<br/>
Wskaźnik do buforu, który odbiera dane wielostrowe. Wielociągowy to tablica ciągów zakończonych wartością null, zakończonych dwoma znakami null.

*PnChars*<br/>
Wielkość, w CZAR, buforu wskazanego przez *pszValue*. Gdy metoda zwraca, *pnChars* zawiera rozmiar, w CZAR, wielociągowy pobranych, w tym kończący się znak null.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, ERROR_SUCCESS jest zwracany. Jeśli metoda nie odczytuje wartości, zwraca kod błędu niezerowego zdefiniowany w WINERROR. H. Jeśli dane, do których się odwołuje, nie są REG_MULTI_SZ typu, zwracany jest ERROR_INVALID_DATA.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta `RegQueryValueEx` i potwierdza, że zwracany jest poprawny typ danych. Zobacz [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) aby uzyskać więcej informacji.

> [!IMPORTANT]
> Ta metoda umożliwia wywołującemu określić dowolną lokalizację rejestru, potencjalnie odczytywania danych, których nie można ufać. Ponadto [Funkcja RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone wartością NULL. Oba warunki powinny być sprawdzane przez kod wywołujący.

## <a name="cregkeyqueryqwordvalue"></a><a name="queryqwordvalue"></a>CRegKey::QueryQWORDValue

Wywołanie tej metody, aby pobrać dane QWORD dla określonej nazwy wartości.

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik do ciągu zakończonego wartością null zawierającego nazwę wartości do kwerendy.

*wartość qw*<br/>
Wskaźnik do buforu, który odbiera QWORD.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, ERROR_SUCCESS jest zwracany. Jeśli metoda nie odczytuje wartości, zwraca kod błędu niezerowego zdefiniowany w WINERROR. H. Jeśli dane, do których się odwołuje, nie są REG_QWORD typu, zwracany jest ERROR_INVALID_DATA.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta `RegQueryValueEx` i potwierdza, że zwracany jest poprawny typ danych. Zobacz [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) aby uzyskać więcej informacji.

> [!IMPORTANT]
> Ta metoda umożliwia wywołującemu określić dowolną lokalizację rejestru, potencjalnie odczytywania danych, których nie można ufać. Ponadto [Funkcja RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone wartością NULL. Oba warunki powinny być sprawdzane przez kod wywołujący.

## <a name="cregkeyquerystringvalue"></a><a name="querystringvalue"></a>CRegKey::QueryStringValue

Wywołanie tej metody, aby pobrać dane ciągu dla określonej nazwy wartości.

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik do ciągu zakończonego wartością null zawierającego nazwę wartości do kwerendy.

*pszValue (właskw.*<br/>
Wskaźnik do buforu, który odbiera dane ciągu.

*PnChars*<br/>
Wielkość, w CZAR, buforu wskazanego przez *pszValue*. Gdy metoda zwraca, *pnChars* zawiera rozmiar, w CZAR, ciągu pobranego, w tym kończący się znak null.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, ERROR_SUCCESS jest zwracany. Jeśli metoda nie odczytuje wartości, zwraca kod błędu niezerowego zdefiniowany w WINERROR. H. Jeśli dane, do których się odwołuje, nie są REG_SZ typu, zwracany jest ERROR_INVALID_DATA. Jeśli metoda zwraca ERROR_MORE_DATA, *pnChars* jest równa zero, a nie wymagany rozmiar buforu w bajtach.

### <a name="remarks"></a>Uwagi

Ta metoda korzysta `RegQueryValueEx` i potwierdza, że zwracany jest poprawny typ danych. Zobacz [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) aby uzyskać więcej informacji.

> [!IMPORTANT]
> Ta metoda umożliwia wywołującemu określić dowolną lokalizację rejestru, potencjalnie odczytywania danych, których nie można ufać. Ponadto [Funkcja RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone wartością NULL. Oba warunki powinny być sprawdzane przez kod wywołujący.

## <a name="cregkeyqueryvalue"></a><a name="queryvalue"></a>CRegKey::QueryValue

Wywołanie tej metody, aby pobrać dane dla określonego pola wartości [m_hKey](#m_hkey). Wcześniejsze wersje tej metody nie są już obsługiwane i są oznaczone jako ATL_DEPRECATED.

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
Wskaźnik do ciągu zakończonego wartością null zawierającego nazwę wartości do kwerendy. Jeśli *pszValueName* jest NULL lub pusty ciąg ,"", metoda pobiera typ i dane dla klucza bez nazwy lub wartości domyślnej, jeśli istnieje.

*pdwTyp*<br/>
Wskaźnik do zmiennej, która odbiera kod wskazujący typ danych przechowywanych w określonej wartości. Parametr *pdwType* może mieć wartość NULL, jeśli kod typu nie jest wymagany.

*Pdata*<br/>
Wskaźnik do buforu, który odbiera dane wartości. Ten parametr może mieć wartość NULL, jeśli dane nie są wymagane.

*PnBytes ( pnBytes )*<br/>
Wskaźnik do zmiennej, która określa rozmiar w bajtach buforu wskazywać przez parametr *pData.* Gdy metoda zwraca, ta zmienna zawiera rozmiar danych skopiowanych do *pData.*

*dwValue (Wartość dwValue)*<br/>
Dane liczbowe pola wartości.

*lpszValueName*<br/>
Określa pole wartości, które ma zostać zapytane.

*szValue (szValue)*<br/>
Dane ciągu pola wartości.

*pdwCount (liczba pdwCount)*<br/>
Rozmiar danych ciągu. Jego wartość jest początkowo ustawiona na rozmiar *buforu szValue.*

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie kod błędu niezerowego zdefiniowany w WINERROR. H.

### <a name="remarks"></a>Uwagi

Dwie oryginalne wersje `QueryValue` nie są już obsługiwane i są oznaczone jako ATL_DEPRECATED. Kompilator wyda ostrzeżenie, jeśli te formularze są używane.

Pozostała metoda wywołuje RegQueryValueEx.

> [!IMPORTANT]
> Ta metoda umożliwia wywołującemu określić dowolną lokalizację rejestru, potencjalnie odczytywania danych, których nie można ufać. Ponadto Funkcja RegQueryValueEx używana przez tę metodę nie obsługuje jawnie ciągów, które są zakończone wartością NULL. Oba warunki powinny być sprawdzane przez kod wywołujący.

## <a name="cregkeyrecursedeletekey"></a><a name="recursedeletekey"></a>CRegKey::RecurseDeleteKey

Wywołanie tej metody, aby usunąć określony klucz z rejestru i jawnie usunąć wszystkie podkluczy.

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>Parametry

*lpszKey (klawisz)*<br/>
Określa nazwę klucza do usunięcia. Ta nazwa musi być podkluczem [m_hKey](#m_hkey).

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie wartość błędu niezerowego zdefiniowana w WINERROR. H.

### <a name="remarks"></a>Uwagi

Jeśli klucz ma podkluczy, należy wywołać tę metodę, aby usunąć klucz.

## <a name="cregkeysetbinaryvalue"></a><a name="setbinaryvalue"></a>CRegKey::SetBinaryValue

Wywołanie tej metody, aby ustawić wartość binarną klucza rejestru.

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik do ciągu zawierającego nazwę wartości do ustawionego. Jeśli wartość o tej nazwie nie jest jeszcze obecny, metoda dodaje go do klucza.

*wartość pValue*<br/>
Wskaźnik do buforu zawierającego dane, które mają być przechowywane z określoną nazwą wartości.

*n Bajty*<br/>
Określa rozmiar w bajtach informacji wskazywalnych przez parametr *pValue.*

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w WINERROR. H.

### <a name="remarks"></a>Uwagi

Ta metoda używa [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) do zapisu wartości w rejestrze.

## <a name="cregkeysetdwordvalue"></a><a name="setdwordvalue"></a>CRegKey::SetDWORDValue

Wywołanie tej metody, aby ustawić wartość DWORD klucza rejestru.

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik do ciągu zawierającego nazwę wartości do ustawionego. Jeśli wartość o tej nazwie nie jest jeszcze obecny, metoda dodaje go do klucza.

*dwValue (Wartość dwValue)*<br/>
Dane DWORD, które mają być przechowywane z określoną nazwą wartości.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w WINERROR. H.

### <a name="remarks"></a>Uwagi

Ta metoda używa [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) do zapisu wartości w rejestrze.

## <a name="cregkeysetguidvalue"></a><a name="setguidvalue"></a>CRegKey::SetGUIDValue

Wywołanie tej metody, aby ustawić wartość GUID klucza rejestru.

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik do ciągu zawierającego nazwę wartości do ustawionego. Jeśli wartość o tej nazwie nie jest jeszcze obecny, metoda dodaje go do klucza.

*wartość guidValue*<br/>
Odwołanie do identyfikatora GUID, który ma być przechowywany z określoną nazwą wartości.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w WINERROR. H.

### <a name="remarks"></a>Uwagi

Ta metoda wykorzystuje `CRegKey::SetStringValue` i konwertuje identyfikator GUID na ciąg przy użyciu [StringFromGUID2](/windows/win32/api/combaseapi/nf-combaseapi-stringfromguid2).

## <a name="cregkeysetkeyvalue"></a><a name="setkeyvalue"></a>CRegKey::SetKeyValue

Wywołanie tej metody do przechowywania danych w określonym polu wartości określonego klucza.

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>Parametry

*lpszKeyName (Nazwa_*<br/>
Określa nazwę klucza, który ma zostać utworzony lub otwarty. Ta nazwa musi być podkluczem [m_hKey](#m_hkey).

*lpszValue*<br/>
Określa dane, które mają być przechowywane. Ten parametr musi być nienawiązany do wartości NULL.

*lpszValueName*<br/>
Określa pole wartości, które ma zostać ustawione. Jeśli pole wartości o tej nazwie jeszcze nie istnieje w kluczu, zostanie dodane.

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie kod błędu niezerowego zdefiniowany w WINERROR. H.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby utworzyć lub otworzyć klucz *lpszKeyName* i przechowywać dane *lpszValue* w polu wartości *lpszValueName.*

## <a name="cregkeysetkeysecurity"></a><a name="setkeysecurity"></a>CRegKey::SetKeySecurity

Wywołanie tej metody, aby ustawić bezpieczeństwo klucza rejestru.

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>Parametry

*Si*<br/>
Określa składniki deskryptora zabezpieczeń do ustawienia. Wartość może być kombinacją następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|Ustawia dyskrecjonacyjną listę kontroli dostępu klucza (DACL). Klucz musi mieć WRITE_DAC dostęp lub proces wywołujący musi być właścicielem obiektu.|
|GROUP_SECURITY_INFORMATION|Ustawia identyfikator zabezpieczeń grupy podstawowej klucza (SID). Klucz musi mieć WRITE_OWNER dostęp lub proces wywołujący musi być właścicielem obiektu.|
|OWNER_SECURITY_INFORMATION|Ustawia identyfikator SID właściciela klucza. Klucz musi mieć WRITE_OWNER dostęp lub proces wywołujący musi być właścicielem obiektu lub mieć włączone uprawnienie SE_TAKE_OWNERSHIP_NAME.|
|SACL_SECURITY_INFORMATION|Ustawia listę kontroli dostępu do systemu klucza (SACL). Klucz musi mieć ACCESS_SYSTEM_SECURITY dostęp. Właściwym sposobem uzyskania tego dostępu jest włączenie [uprawnień](/windows/win32/secauthz/privileges) SE_SECURITY_NAME w bieżącym tokenie dostępu wywołującego, otwarcie dojścia dla ACCESS_SYSTEM_SECURITY dostępu, a następnie wyłączenie uprawnienia.|

*Psd*<br/>
Wskaźnik do [struktury SECURITY_DESCRIPTOR,](/windows/win32/api/winnt/ns-winnt-security_descriptor) która określa atrybuty zabezpieczeń, które należy ustawić dla określonego klucza.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w WINERROR. H.

### <a name="remarks"></a>Uwagi

Ustawia atrybuty zabezpieczeń klucza. Zobacz [RegSetKeySecurity](/windows/win32/api/winreg/nf-winreg-regsetkeysecurity) aby uzyskać więcej informacji.

## <a name="cregkeysetmultistringvalue"></a><a name="setmultistringvalue"></a>CRegKey::SetMultiStringValue

Wywołanie tej metody, aby ustawić wartość wielociągową klucza rejestru.

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik do ciągu zawierającego nazwę wartości do ustawionego. Jeśli wartość o tej nazwie nie jest jeszcze obecny, metoda dodaje go do klucza.

*pszValue (właskw.*<br/>
Wskaźnik do danych wielościowych, które mają być przechowywane z określoną nazwą wartości. Wielociągowy to tablica ciągów zakończonych wartością null, zakończonych dwoma znakami null.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w WINERROR. H.

### <a name="remarks"></a>Uwagi

Ta metoda używa [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) do zapisu wartości w rejestrze.

## <a name="cregkeysetqwordvalue"></a><a name="setqwordvalue"></a>CRegKey::SetQWORDValue

Wywołanie tej metody, aby ustawić wartość QWORD klucza rejestru.

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik do ciągu zawierającego nazwę wartości do ustawionego. Jeśli wartość o tej nazwie nie jest jeszcze obecny, metoda dodaje go do klucza.

*wartość qw*<br/>
Dane QWORD, które mają być przechowywane z określoną nazwą wartości.

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w WINERROR. H.

### <a name="remarks"></a>Uwagi

Ta metoda używa [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) do zapisu wartości w rejestrze.

## <a name="cregkeysetstringvalue"></a><a name="setstringvalue"></a>CRegKey::SetStringValue

Wywołanie tej metody, aby ustawić wartość ciągu klucza rejestru.

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>Parametry

*pszValueName*<br/>
Wskaźnik do ciągu zawierającego nazwę wartości do ustawionego. Jeśli wartość o tej nazwie nie jest jeszcze obecny, metoda dodaje go do klucza.

*pszValue (właskw.*<br/>
Wskaźnik do danych ciągu, które mają być przechowywane z określoną nazwą wartości.

*dwType (typ)*<br/>
Typ ciągu do zapisu w rejestrze: REG_SZ (wartość domyślna) lub REG_EXPAND_SZ (dla wielostrunowych).

### <a name="return-value"></a>Wartość zwracana

Jeśli metoda powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli metoda nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w WINERROR. H.

### <a name="remarks"></a>Uwagi

Ta metoda używa [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) do zapisu wartości w rejestrze.

## <a name="cregkeysetvalue"></a><a name="setvalue"></a>CRegKey::SetValue

Wywołanie tej metody do przechowywania danych w określonym polu wartości [m_hKey](#m_hkey). Wcześniejsze wersje tej metody nie są już obsługiwane i są oznaczone jako ATL_DEPRECATED.

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
Wskaźnik do ciągu zawierającego nazwę wartości do ustawionego. Jeśli wartość o tej nazwie nie jest jeszcze obecny w kluczu, metoda dodaje go do klucza. Jeśli *pszValueName* ma wartość NULL lub pusty ciąg "", metoda ustawia typ i dane dla wartości bez nazwy lub wartości domyślnej klucza.

*dwType (typ)*<br/>
Określa kod wskazujący typ danych wskazywalnych przez parametr *pValue.*

*wartość pValue*<br/>
Wskaźnik do buforu zawierającego dane, które mają być przechowywane z określoną nazwą wartości.

*n Bajty*<br/>
Określa rozmiar w bajtach informacji wskazywalnych przez parametr *pValue.* Jeśli dane mają typ REG_SZ, REG_EXPAND_SZ lub REG_MULTI_SZ, *nBytes* musi zawierać rozmiar kończącego się znaku null.

*hKeyParent*<br/>
Uchwyt otwartego klucza.

*lpszKeyName (Nazwa_*<br/>
Określa nazwę klucza, który ma zostać utworzony lub otwarty. Ta nazwa musi być podkluczem *hKeyParent*.

*lpszValue*<br/>
Określa dane, które mają być przechowywane. Ten parametr musi być nienawiązany do wartości NULL.

*lpszValueName*<br/>
Określa pole wartości, które ma zostać ustawione. Jeśli pole wartości o tej nazwie jeszcze nie istnieje w kluczu, zostanie dodane.

*dwValue (Wartość dwValue)*<br/>
Określa dane, które mają być przechowywane.

*bMulti*<br/>
Jeśli false, wskazuje, że ciąg jest typu REG_SZ. Jeśli true, wskazuje, że ciąg jest wielostrunowy typu REG_MULTI_SZ.

*nValueLen (Wartość)*<br/>
Jeśli *bMulti* jest true, *nValueLen* jest długość *ciągu lpszValue* znaków. Jeśli *bMulti* jest false, wartość -1 wskazuje, że metoda obliczy długość automatycznie.

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca ERROR_SUCCESS; w przeciwnym razie kod błędu niezerowego zdefiniowany w WINERROR. H.

### <a name="remarks"></a>Uwagi

Dwie oryginalne wersje `SetValue` są oznaczone jako ATL_DEPRECATED i nie powinny być już używane. Kompilator wyda ostrzeżenie, jeśli te formularze są używane.

Trzecia metoda wywołuje [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw).

## <a name="see-also"></a>Zobacz też

[Próbka DCOM](../../overview/visual-cpp-samples.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
