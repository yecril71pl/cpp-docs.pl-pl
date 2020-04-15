---
title: Klasa CSettingsStore
ms.date: 11/04/2016
f1_keywords:
- CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::Close
- AFXSETTINGSSTORE/CSettingsStore::CreateKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteValue
- AFXSETTINGSSTORE/CSettingsStore::Open
- AFXSETTINGSSTORE/CSettingsStore::Read
- AFXSETTINGSSTORE/CSettingsStore::Write
helpviewer_keywords:
- CSettingsStore [MFC], CSettingsStore
- CSettingsStore [MFC], Close
- CSettingsStore [MFC], CreateKey
- CSettingsStore [MFC], DeleteKey
- CSettingsStore [MFC], DeleteValue
- CSettingsStore [MFC], Open
- CSettingsStore [MFC], Read
- CSettingsStore [MFC], Write
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
ms.openlocfilehash: b1acf959c371aa23ac55ace7fea9466f0e20813f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318469"
---
# <a name="csettingsstore-class"></a>Klasa CSettingsStore

Zawija funkcje interfejsu API systemu Windows, zapewniając interfejs obiektowy używany do uzyskiwania dostępu do rejestru.

## <a name="syntax"></a>Składnia

```
class CSettingsStore : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSettingsStore::CSettingsStore](#csettingsstore)|Konstruuje `CSettingsStore` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSettingsStore::Zamknij](#close)|Zamyka otwarty klucz rejestru.|
|[CSettingsStore::CreateKey](#createkey)|Otwiera określony klucz lub tworzy go, jeśli nie istnieje.|
|[CSettingsStore::DeleteKey](#deletekey)|Usuwa określony klucz i wszystkie jego wiązki obrażeń.|
|[CSettingsStore::DeleteValue](#deletevalue)|Usuwa określoną wartość otwartego klucza.|
|[CSettingsStore::Otwórz](#open)|Otwiera określony klucz.|
|[CSettingsStore::Czytaj](#read)|Pobiera dane dla określonej wartości klucza.|
|[CSettingsStore::Napisz](#write)|Zapisuje wartość do rejestru pod kluczem otwartym.|

## <a name="remarks"></a>Uwagi

Element członkowski działa `CreateKey` i `Open` są bardzo podobne. Jeśli klucz rejestru już `CreateKey` istnieje `Open` i działa w ten sam sposób. Jednak jeśli klucz rejestru nie `CreateKey` istnieje, utworzy `Open` go, podczas gdy zwróci wartość błędu.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `CSettingsStore` Open i Read metody klasy. Ten fragment kodu jest częścią [przykładu Demo etykietki narzędzia](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxsettingsstore.h

## <a name="csettingsstoreclose"></a><a name="close"></a>CSettingsStore::Zamknij

Zamyka otwarty klucz rejestru.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda jest wywoływana z destruktora [CSettingsStore Klasy](../../mfc/reference/csettingsstore-class.md).

## <a name="csettingsstorecreatekey"></a><a name="createkey"></a>CSettingsStore::CreateKey

Otwiera klucz rejestru lub tworzy go, jeśli nie istnieje.

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parametry

*PSZPath*<br/>
[w] Określa nazwę klucza, który ma zostać utworzony lub otwarty.

### <a name="return-value"></a>Wartość zwracana

0 w przypadku powodzenia; w przeciwnym razie wartość niezerowa.

### <a name="remarks"></a>Uwagi

`CreateKey`jako `m_hKey` źródło zapytań rejestru. Wyszukuje *pszPath* jako `m_hKey`podklucz . Jeśli klucz nie istnieje, `CreateKey` tworzy go. W przeciwnym razie otwiera klucz. `CreateKey`następnie `m_hKey` ustawia klucz utworzony lub otwarty.

## <a name="csettingsstorecsettingsstore"></a><a name="csettingsstore"></a>CSettingsStore::CSettingsStore

Tworzy obiekt `CSettngsStore`.

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Parametry

*bDmin*<br/>
[w] Parametr logiczny określający, `CSettingsStore` czy obiekt działa w trybie administratora.

*bCzytyNie*<br/>
[w] Parametr logiczny określający, `CSettingsStore` czy obiekt jest tworzony w trybie tylko do odczytu.

### <a name="remarks"></a>Uwagi

Jeśli *bAdmin* jest ustawiona `m_hKey` na WARTOŚĆ PRAWDA, zmienna elementu członkowskiego jest ustawiona na **HKEY_LOCAL_MACHINE**. Jeśli ustawisz *bAdmin* na FAŁSZ, `m_hKey` jest ustawiona na **HKEY_CURRENT_USER**.

Dostęp do zabezpieczeń zależy od parametru *bReadOnly.* Jeśli *bTylko* jest FALSE, dostęp do zabezpieczeń zostanie ustawiony na **KEY_ALL_ACCESS**. Jeśli *bTylko* jest TRUE, dostęp do zabezpieczeń zostanie ustawiony na kombinację **KEY_QUERY_VALUE, KEY_NOTIFY** i **KEY_ENUMERATE_SUB_KEYS**. Aby uzyskać więcej informacji na temat dostępu do zabezpieczeń wraz z rejestrem, zobacz [Zabezpieczenia klucza rejestru i prawa dostępu](/windows/win32/SysInfo/registry-key-security-and-access-rights).

Destruktor do `CSettingsStore` `m_hKey` wydań automatycznie.

## <a name="csettingsstoredeletekey"></a><a name="deletekey"></a>CSettingsStore::DeleteKey

Usuwa klucz i wszystkie jego wiązki łzowe z rejestru.

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>Parametry

*PSZPath*<br/>
[w] Nazwa klucza do usunięcia.

*bDmin*<br/>
[w] Przełącznik, który określa lokalizację klucza do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda zakończy `CSettingsStore` się niepowodzeniem, jeśli obiekt jest w trybie tylko do odczytu.

Jeśli parametr *bAdmin* wynosi `DeleteKey` zero, wyszuka klucz do usunięcia w obszarze **HKEY_CURRENT_USER**. Jeśli *bAdmin* nie ma `DeleteKey` wartościzerowej, wyszukaj klucz do usunięcia w obszarze **HKEY_LOCAL_MACHINE**.

## <a name="csettingsstoredeletevalue"></a><a name="deletevalue"></a>CSettingsStore::DeleteValue

Usuwa wartość z `m_hKey`pliku .

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>Parametry

*pszValue (właskw.*<br/>
[w] Określa pole wartości do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

## <a name="csettingsstoreopen"></a><a name="open"></a>CSettingsStore::Otwórz

Otwiera klucz rejestru.

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parametry

*PSZPath*<br/>
[w] Nazwa klucza rejestru.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po pomyślnym otwarciu tej metody `m_hKey` określony klucz, ustawia dojścia tego klucza.

## <a name="csettingsstoreread"></a><a name="read"></a>CSettingsStore::Czytaj

Odczytuje wartość z klucza w rejestrze.

```
virtual BOOL Read(
    LPCTSTR pszKey,
    int& iVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    DWORD& dwVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CString& sVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Read(
    LPCTSTR pszKey,
    CRect& rect);

virtual BOOL Read(
    LPCTSTR pszKey,
    BYTE** ppData,
    UINT* pBytes);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject*& pObj);
```

### <a name="parameters"></a>Parametry

*pszKey (własówce)*<br/>
[w] Wskaźnik do ciągu zakończonego zerem, który zawiera nazwę wartości do odczytu z rejestru.

*iVal ( iVal )*<br/>
[na zewnątrz] Odwołanie do zmiennej całkowitej, która odbiera wartość odczytu z klucza rejestru.

*Dwval*<br/>
[na zewnątrz] Odwołanie do 32-bitowej zmiennej dwusłowa, która odbiera wartość odczytywana z klucza rejestru.

*sVal (sVal)*<br/>
[na zewnątrz] Odwołanie do zmiennej ciągu, która odbiera wartość odczytu z klucza rejestru.

*lista scString*<br/>
[na zewnątrz] Odwołanie do zmiennej listy ciągów, która odbiera wartość odczytu z klucza rejestru.

*scArray (scArray)*<br/>
[na zewnątrz] Odwołanie do zmiennej tablicy ciągów, która odbiera wartość odczytu z klucza rejestru.

*dwcArray (Polski)*<br/>
[na zewnątrz] Odwołanie do 32-bitowej zmiennej tablicy podwójnego wyrazu, która odbiera wartość odczytywana z klucza rejestru.

*wcArray*<br/>
[na zewnątrz] Odwołanie do 16-bitowej zmiennej tablicowej wyrazów, która odbiera wartość odczytywana z klucza rejestru.

*bcArray ( bcArray )*<br/>
[na zewnątrz] Odwołanie do zmiennej tablicy bajtów, która odbiera wartość odczytu z klucza rejestru.

*lpPoint (punkt z punktu widzenia*<br/>
[na zewnątrz] Odwołanie do wskaźnika `POINT` do struktury, która odbiera wartość odczytu z klucza rejestru.

*Rect*<br/>
[na zewnątrz] Odwołanie do zmiennej [CRect,](../../atl-mfc-shared/reference/crect-class.md) która odbiera wartość odczytu z klucza rejestru.

*ppData (dane)*<br/>
[na zewnątrz] Wskaźnik do wskaźnika do danych, które odbiera wartość odczytu z klucza rejestru.

*p Bajty*<br/>
[na zewnątrz] Wskaźnik do niepodpisanej zmiennej całkowitej. Ta zmienna odbiera rozmiar buforu, który *ppData* wskazuje.

*list*<br/>
[na zewnątrz] Odwołanie do zmiennej [CObList,](../../mfc/reference/coblist-class.md) która odbiera wartość odczytu z klucza rejestru.

*Obj*<br/>
[na zewnątrz] Odwołanie do zmiennej [CObject,](../../mfc/reference/cobject-class.md) która odbiera wartość odczytu z klucza rejestru.

*pObj*<br/>
[na zewnątrz] Odwołanie do wskaźnika `CObject` do zmiennej, która odbiera wartość odczytu z klucza rejestru.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`Read`sprawdza *pszKey* jako podklucz . `m_hKey`

## <a name="csettingsstorewrite"></a><a name="write"></a>CSettingsStore::Napisz

Zapisuje wartość do rejestru pod kluczem otwartym.

```
virtual BOOL Write(
    LPCTSTR pszKey,
    int iVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    DWORD dwVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPCTSTR pszVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Write(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    const CRect& rect);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPBYTE pData,
    UINT nBytes);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject* pObj);
```

### <a name="parameters"></a>Parametry

*pszKey (własówce)*<br/>
[w] Wskaźnik do ciągu, który zawiera nazwę wartości do ustawionego.

*iVal ( iVal )*<br/>
[w] Odwołanie do zmiennej całkowitej zawierającej dane do przechowywania.

*Dwval*<br/>
[w] Odwołanie do 32-bitowej zmiennej dwusłowa, która zawiera dane do przechowywania.

*pszVal*<br/>
[w] Wskaźnik do zmiennej ciągu zakończonej wartością null, która zawiera dane do przechowywania.

*lista scString*<br/>
[w] Odwołanie do zmiennej [CStringList,](../../mfc/reference/cstringlist-class.md) która zawiera dane do przechowywania.

*bcArray ( bcArray )*<br/>
[w] Odwołanie do zmiennej tablicy bajtów, która zawiera dane do przechowywania.

*scArray (scArray)*<br/>
[w] Odwołanie do zmiennej tablicy ciągów, która zawiera dane do przechowywania.

*dwcArray (Polski)*<br/>
[w] Odwołanie do 32-bitowej zmiennej tablicy dwusłowa, która zawiera dane do przechowywania.

*wcArray*<br/>
[w] Odwołanie do 16-bitowej zmiennej tablicowej wyrazów, która zawiera dane do przechowywania.

*Rect*<br/>
[w] Odwołanie do zmiennej [CRect,](../../atl-mfc-shared/reference/crect-class.md) która zawiera dane do przechowywania.

*lpPoint (punkt z punktu widzenia*<br/>
[w] Odwołanie do wskaźnika `POINT` do zmiennej, która zawiera dane do przechowywania.

*Pdata*<br/>
[w] Wskaźnik do buforu, który zawiera dane do przechowywania.

*n Bajty*<br/>
[w] Określa rozmiar w bajtach danych, na które wskazuje parametr *pData.*

*list*<br/>
[w] Odwołanie do zmiennej [CObList,](../../mfc/reference/coblist-class.md) która zawiera dane do przechowywania.

*Obj*<br/>
[w] Odwołanie do zmiennej [CObject,](../../mfc/reference/cobject-class.md) która zawiera dane do przechowywania.

*pObj*<br/>
[w] Wskaźnik do wskaźnika `CObject` do zmiennej, która zawiera dane do przechowywania.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Aby zapisać do rejestru, należy ustawić *bReadOnly* do wartości niezerowej podczas tworzenia [obiektu CSettingsStore.](../../mfc/reference/csettingsstore-class.md) Aby uzyskać więcej informacji, zobacz [CSettingsStore::CSettingsStore](#csettingsstore).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)
