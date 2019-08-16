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
ms.openlocfilehash: 75d86b81d9651e5892913af5919ae0a78fe6bbc5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502921"
---
# <a name="csettingsstore-class"></a>Klasa CSettingsStore

Zawija funkcje interfejsu API systemu Windows, zapewniając interfejs zorientowany na obiekt, który służy do uzyskiwania dostępu do rejestru.

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
|[CSettingsStore:: Close](#close)|Zamyka otwarty klucz rejestru.|
|[CSettingsStore:: CreateKey](#createkey)|Otwiera określony klucz lub tworzy go, jeśli nie istnieje.|
|[CSettingsStore::D eleteKey](#deletekey)|Usuwa określony klucz i wszystkie jego elementy podrzędne.|
|[CSettingsStore::DeleteValue](#deletevalue)|Usuwa określoną wartość otwartego klucza.|
|[CSettingsStore:: Open](#open)|Otwiera określony klucz.|
|[CSettingsStore:: Read](#read)|Pobiera dane dla określonej wartości klucza.|
|[CSettingsStore:: Write](#write)|Zapisuje wartość w rejestrze w kluczu otwartym.|

## <a name="remarks"></a>Uwagi

Funkcje `CreateKey` Członkowskie i `Open` są bardzo podobne. Jeśli klucz rejestru już istnieje `CreateKey` i `Open` działa w ten sam sposób. Jeśli jednak klucz rejestru nie istnieje, program utworzy go `CreateKey` , a `Open` następnie zwróci wartość błędu.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób używania metod `CSettingsStore` otwierania i odczytywania klasy. Ten fragment kodu jest częścią [przykładu pokazu etykietki narzędzia](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxsettingsstore. h

##  <a name="close"></a>CSettingsStore:: Close

Zamyka otwarty klucz rejestru.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda jest wywoływana z destruktora [klasy CSettingsStore](../../mfc/reference/csettingsstore-class.md).

##  <a name="createkey"></a>CSettingsStore:: CreateKey

Otwiera klucz rejestru lub tworzy go, jeśli nie istnieje.

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parametry

*pszPath*<br/>
podczas Określa nazwę klucza, który ma zostać utworzony lub otwarty.

### <a name="return-value"></a>Wartość zwracana

0, jeśli pomyślne; w przeciwnym razie wartość różna od zera.

### <a name="remarks"></a>Uwagi

`CreateKey`używa `m_hKey` jako głównego zapytania dotyczącego rejestru. Szuka *pszPath* jako podklucza `m_hKey`. Jeśli klucz nie istnieje, `CreateKey` tworzy go. W przeciwnym razie zostanie otwarty klucz. `CreateKey`następnie ustawia `m_hKey` na utworzony lub otwarty klucz.

##  <a name="csettingsstore"></a>CSettingsStore::CSettingsStore

`CSettngsStore` Tworzy obiekt.

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Parametry

*bAdmin*<br/>
podczas Wartość logiczna określająca, czy `CSettingsStore` obiekt działa w trybie administratora.

*bReadOnly*<br/>
podczas Wartość logiczna określająca, czy `CSettingsStore` obiekt jest tworzony w trybie tylko do odczytu.

### <a name="remarks"></a>Uwagi

Jeśli *bAdmin* ma wartość true, `m_hKey` zmienna członkowska jest ustawiona na **HKEY_LOCAL_MACHINE**. Jeśli ustawisz *bAdmin* na false, `m_hKey` jest ustawiony na **HKEY_CURRENT_USER**.

Dostęp zabezpieczeń zależy od parametru *bReadOnly* . Jeśli *bReadOnly* ma wartość false, dostęp zabezpieczeń zostanie ustawiony na **KEY_ALL_ACCESS**. Jeśli *bReadyOnly* ma wartość true, dostęp zabezpieczeń zostanie ustawiony na kombinację **KEY_QUERY_VALUE, KEY_NOTIFY** i **KEY_ENUMERATE_SUB_KEYS**. Aby uzyskać więcej informacji o dostępie do rejestru, zobacz [zabezpieczenia klucza rejestru i prawa dostępu](/windows/win32/SysInfo/registry-key-security-and-access-rights).

Destruktor dla `CSettingsStore` wydań `m_hKey` jest automatycznie.

##  <a name="deletekey"></a>CSettingsStore::D eleteKey

Usuwa klucz i wszystkie jego elementy podrzędne z rejestru.

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>Parametry

*pszPath*<br/>
podczas Nazwa klucza do usunięcia.

*bAdmin*<br/>
podczas Przełącznik określający lokalizację klucza do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda zakończy się niepowodzeniem, `CSettingsStore` Jeśli obiekt jest w trybie tylko do odczytu.

Jeśli parametr *bAdmin* ma wartość zero, `DeleteKey` wyszukuje klucz do usunięcia w sekcji **HKEY_CURRENT_USER**. Jeśli *bAdmin* ma wartość różną od `DeleteKey` zera, wyszukuje klucz do usunięcia w sekcji **HKEY_LOCAL_MACHINE**.

##  <a name="deletevalue"></a>CSettingsStore::D eleteValue

Usuwa wartość z `m_hKey`.

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>Parametry

*pszValue*<br/>
podczas Określa pole wartości do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

##  <a name="open"></a>CSettingsStore:: Open

Otwiera klucz rejestru.

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parametry

*pszPath*<br/>
podczas Nazwa klucza rejestru.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po pomyślnym otwarciu określonego klucza przez tę metodę jest `m_hKey` on ustawiany na dojście tego klucza.

##  <a name="read"></a>CSettingsStore:: Read

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

*pszKey*<br/>
podczas Wskaźnik na ciąg zakończony znakiem null, który zawiera nazwę wartości, która ma zostać odczytana z rejestru.

*iVal*<br/>
określoną Odwołanie do zmiennej całkowitej, która otrzymuje wartość odczytaną z klucza rejestru.

*dwVal*<br/>
określoną Odwołanie do 32-bitowej podwójnej zmiennej słowa, która otrzymuje wartość odczytaną z klucza rejestru.

*sVal*<br/>
określoną Odwołanie do zmiennej ciągu, która otrzymuje wartość odczytaną z klucza rejestru.

*scStringList*<br/>
określoną Odwołanie do zmiennej listy ciągów, która otrzymuje wartość odczytaną z klucza rejestru.

*scArray*<br/>
określoną Odwołanie do zmiennej tablicy ciągów, która otrzymuje wartość odczytaną z klucza rejestru.

*dwcArray*<br/>
określoną Odwołanie do 32-bitowej podwójnej zmiennej tablicowej programu Word, która otrzymuje wartość odczytaną z klucza rejestru.

*wcArray*<br/>
określoną Odwołanie do 16-bitowej zmiennej tablicowej programu Word, która otrzymuje wartość odczytaną z klucza rejestru.

*bcArray*<br/>
określoną Odwołanie do zmiennej tablicowej Byte, która otrzymuje wartość odczytaną z klucza rejestru.

*lpPoint*<br/>
określoną Odwołanie do wskaźnika do `POINT` struktury, która otrzymuje wartość odczytaną z klucza rejestru.

*cinania*<br/>
określoną Odwołanie do zmiennej [CRect](../../atl-mfc-shared/reference/crect-class.md) , która otrzymuje wartość odczytaną z klucza rejestru.

*ppData*<br/>
określoną Wskaźnik na wskaźnik do danych, który odbiera wartość odczytywaną z klucza rejestru.

*pBytes*<br/>
określoną Wskaźnik do zmiennej niepodpisanej liczby całkowitej. Ta zmienna otrzymuje rozmiar buforu, do którego wskazuje *ppData* .

*list*<br/>
określoną Odwołanie do zmiennej [CObList](../../mfc/reference/coblist-class.md) , która otrzymuje wartość odczytaną z klucza rejestru.

*obj*<br/>
określoną Odwołanie do zmiennej [CObject](../../mfc/reference/cobject-class.md) , która otrzymuje wartość odczytaną z klucza rejestru.

*pObj*<br/>
określoną Odwołanie do wskaźnika do `CObject` zmiennej, która otrzymuje wartość odczytaną z klucza rejestru.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`Read`sprawdza *pszKey* jako podklucz `m_hKey`.

##  <a name="write"></a>CSettingsStore:: Write

Zapisuje wartość w rejestrze w kluczu otwartym.

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

*pszKey*<br/>
podczas Wskaźnik na ciąg, który zawiera nazwę wartości do ustawienia.

*iVal*<br/>
podczas Odwołanie do zmiennej całkowitej, która zawiera dane do przechowywania.

*dwVal*<br/>
podczas Odwołanie do 32-bitowej podwójnej zmiennej słowa, która zawiera dane do przechowywania.

*pszVal*<br/>
podczas Wskaźnik do zmiennej ciągu z zakończono wartością null, która zawiera dane do zapisania.

*scStringList*<br/>
podczas Odwołanie do zmiennej [CStringList](../../mfc/reference/cstringlist-class.md) zawierającej dane do przechowania.

*bcArray*<br/>
podczas Odwołanie do zmiennej tablicowej Byte zawierającej dane do zapisania.

*scArray*<br/>
podczas Odwołanie do zmiennej tablicy ciągów zawierającej dane do zapisania.

*dwcArray*<br/>
podczas Odwołanie do 32-bitowej podwójnej zmiennej tablicowej programu Word, która zawiera dane do przechowywania.

*wcArray*<br/>
podczas Odwołanie do 16-bitowej zmiennej tablicowej programu Word, która zawiera dane do przechowywania.

*cinania*<br/>
podczas Odwołanie do zmiennej [CRect](../../atl-mfc-shared/reference/crect-class.md) zawierającej dane do przechowania.

*lpPoint*<br/>
podczas Odwołanie do wskaźnika do `POINT` zmiennej zawierającej dane do przechowania.

*pData*<br/>
podczas Wskaźnik do buforu zawierającego dane do przechowania.

*nBytes*<br/>
podczas Określa rozmiar (w bajtach) danych, do których *pData* punkty parametrów.

*list*<br/>
podczas Odwołanie do zmiennej [CObList](../../mfc/reference/coblist-class.md) zawierającej dane do przechowania.

*obj*<br/>
podczas Odwołanie do zmiennej [CObject](../../mfc/reference/cobject-class.md) zawierającej dane do przechowania.

*pObj*<br/>
podczas Wskaźnik na wskaźnik do `CObject` zmiennej zawierającej dane do przechowania.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Aby można było zapisywać w rejestrze, należy ustawić *bReadOnly* na wartość różną od zera podczas tworzenia obiektu [CSettingsStore](../../mfc/reference/csettingsstore-class.md) . Aby uzyskać więcej informacji, zobacz [CSettingsStore:: CSettingsStore](#csettingsstore).

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)
