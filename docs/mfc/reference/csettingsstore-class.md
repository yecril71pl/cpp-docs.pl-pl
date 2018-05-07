---
title: Klasa CSettingsStore | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f5ed7d1dad634d330ac857f52d6ef35ef36c9c9a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="csettingsstore-class"></a>Klasa CSettingsStore
Opakowuje funkcje interfejsu API systemu Windows, zapewniając zorientowane obiektowo interfejs, który umożliwia uzyskiwanie dostępu do rejestru.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSettingsStore : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSettingsStore::CSettingsStore](#csettingsstore)|Konstruuje `CSettingsStore` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSettingsStore::Close](#close)|Zamyka otworzyć klucza rejestru.|  
|[CSettingsStore::CreateKey](#createkey)|Otwiera określony klucz lub jeśli nie istnieje, tworzy go.|  
|[CSettingsStore::DeleteKey](#deletekey)|Usuwa określony klucz i wszystkich jego obiektów podrzędnych.|  
|[CSettingsStore::DeleteValue](#deletevalue)|Usuwa podaną wartość otworzyć klucza.|  
|[CSettingsStore::Open](#open)|Otwiera określony klucz.|  
|[CSettingsStore::Read](#read)|Pobiera dane dla określonej wartości klucza.|  
|[CSettingsStore::Write](#write)|Zapisuje wartość rejestru w kluczu otwarte.|  
  
## <a name="remarks"></a>Uwagi  
 Funkcje Członkowskie `CreateKey` i `Open` są bardzo podobne. Jeśli istnieje już klucz rejestru, `CreateKey` i `Open` funkcji w taki sam sposób. Jednakże, jeśli klucz rejestru nie istnieje, `CreateKey` zostanie ona utworzona, podczas gdy `Open` zwróci wartość błędu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia metody otwieranie i Odczyt `CSettingsStore` klasy. Następujący fragment kodu jest częścią [próbka Demo Porada narzędzia](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CSettingsStore`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxsettingsstore.h  
  
##  <a name="close"></a>  CSettingsStore::Close  
 Zamyka otworzyć klucza rejestru.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda jest wywoływana z destruktor [CSettingsStore klasy](../../mfc/reference/csettingsstore-class.md).  
  
##  <a name="createkey"></a>  CSettingsStore::CreateKey  
 Otwiera klucz rejestru lub jeśli nie istnieje, tworzy go.  
  
```  
virtual BOOL CreateKey(LPCTSTR pszPath);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pszPath`  
 Określa nazwę klucza do utworzenia lub otwarcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 0 w przypadku powodzenia; w przeciwnym razie wartość różną od zera.  
  
### <a name="remarks"></a>Uwagi  
 `CreateKey` używa `m_hKey` jako katalog główny rejestru zapytania. Wyszukuje `pszPath` jako podklucz `m_hKey`. Jeśli klucz nie istnieje, `CreateKey` tworzy go. W przeciwnym razie zostanie otwarty klucza. `CreateKey` następnie ustawia `m_hKey` do klucza utworzone lub otwarte.  
  
##  <a name="csettingsstore"></a>  CSettingsStore::CSettingsStore  
 Tworzy `CSettngsStore` obiektu.  
  
```  
CSettingsStore(
    BOOL bAdmin,  
    BOOL bReadOnly);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bAdmin`  
 Parametrów typu Boolean określającą czy `CSettingsStore` obiektu działa w trybie administratora.  
  
 [in] `bReadOnly`  
 Parametrów typu Boolean określającą czy `CSettingsStore` obiekt jest tworzony w trybie tylko do odczytu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bAdmin` ustawiono `true`, `m_hKey` ustawiono zmiennej członkowskiej `HKEY_LOCAL_MACHINE`. Jeśli ustawisz `bAdmin` do `false`, `m_hKey` ma ustawioną wartość `HKEY_CURRENT_USER`.  
  
 Zabezpieczenia dostępu jest zależna od `bReadOnly` parametru. Jeśli `bReadonly` jest `false`, zabezpieczenia dostępu zostaną ustawione na `KEY_ALL_ACCESS`. Jeśli `bReadyOnly` jest `true`, zabezpieczenia dostępu zostaną ustawione na kombinacji `KEY_QUERY_VALUE, KEY_NOTIFY` i `KEY_ENUMERATE_SUB_KEYS`. Aby uzyskać więcej informacji o dostępie wraz z rejestru, zobacz [zabezpieczeń klucza rejestru i prawa dostępu](http://msdn.microsoft.com/library/windows/desktop/ms724878).  
  
 Destruktor dla elementu `CSettingsStore` zwalnia `m_hKey` automatycznie.  
  
##  <a name="deletekey"></a>  CSettingsStore::DeleteKey  
 Usuwa z rejestru klucza i wszystkich jego obiektów podrzędnych.  
  
```  
virtual BOOL DeleteKey(
    LPCTSTR pszPath,  
    BOOL bAdmin = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pszPath`  
 Nazwa klucza do usunięcia.  
  
 [in] `bAdmin`  
 Przełącznik, który określa lokalizację klucza do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zakończy się niepowodzeniem, jeśli `CSettingsStore` obiekt jest w trybie tylko do odczytu.  
  
 Jeśli parametr `bAdmin` wynosi zero, `DeleteKey` wyszukuje klucz do usunięcia w obszarze `HKEY_CURRENT_USER`. Jeśli `bAdmin` jest różna od zera, `DeleteKey` wyszukuje klucz do usunięcia w obszarze `HKEY_LOCAL_MACHINE`.  
  
##  <a name="deletevalue"></a>  CSettingsStore::DeleteValue  
 Usuwa wartość z zakresu od `m_hKey`.  
  
```  
virtual BOOL DeleteValue(LPCTSTR pszValue);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pszValue`  
 Określa pole wartości do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
##  <a name="open"></a>  CSettingsStore::Open  
 Otwiera klucz rejestru.  
  
```  
virtual BOOL Open(LPCTSTR pszPath);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pszPath`  
 Nazwa klucza rejestru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Po tej metody pomyślnie otwiera określony klucz, ustawia `m_hKey` do realizacji tego klucza.  
  
##  <a name="read"></a>  CSettingsStore::Read  
 Odczytuje wartości z klucza rejestru.  
  
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
 [in] `pszKey`  
 Wskaźnik do zerem ciąg, który zawiera nazwę wartości, które można odczytać z rejestru.  
  
 [out] `iVal`  
 Odwołanie do zmiennej liczba całkowita, która otrzymuje wartość odczytać z klucza rejestru.  
  
 [out] `dwVal`  
 Odwołanie do zmiennej 32-bitowe o podwójnej precyzji word, który odbiera wartość odczytać z klucza rejestru.  
  
 [out] `sVal`  
 Odwołanie do zmiennej ciągu, który odbiera wartość odczytać z klucza rejestru.  
  
 [out] `scStringList`  
 Odwołanie do zmiennej listy ciąg, który odbiera wartość odczytać z klucza rejestru.  
  
 [out] `scArray`  
 Odwołanie do zmiennej tablicy ciąg, który odbiera wartość odczytać z klucza rejestru.  
  
 [out] `dwcArray`  
 Odwołanie do zmiennej tablicy 32-bitowe o podwójnej precyzji word, który odbiera wartość odczytać z klucza rejestru.  
  
 [out] `wcArray`  
 Odwołanie do zmiennej tablicy word 16-bitowych, która otrzymuje wartość odczytać z klucza rejestru.  
  
 [out] `bcArray`  
 Odwołanie do zmiennej tablicy typu byte, która otrzymuje wartość odczytać z klucza rejestru.  
  
 [out] `lpPoint`  
 Odwołanie do wskaźnika do `POINT` odczytać struktury, która otrzymuje wartość z klucza rejestru.  
  
 [out] `rect`  
 Odwołanie do [CRect](../../atl-mfc-shared/reference/crect-class.md) zmienna, która odbiera wartość odczytać z klucza rejestru.  
  
 [out] `ppData`  
 Wskaźnik na wskaźnik do danych, który odbiera wartość odczytu z klucza rejestru.  
  
 [out] `pBytes`  
 Wskaźnik do zmiennej liczby całkowitej bez znaku. Ta zmienna odbiera rozmiar buforu który `ppData` wskazuje.  
  
 [out] `list`  
 Odwołanie do [CObList](../../mfc/reference/coblist-class.md) zmienna, która odbiera wartość odczytać z klucza rejestru.  
  
 [out] `obj`  
 Odwołanie do [CObject](../../mfc/reference/cobject-class.md) zmienna, która odbiera wartość odczytać z klucza rejestru.  
  
 [out] `pObj`  
 Odwołanie do wskaźnika do `CObject` zmienna, która odbiera wartość odczytać z klucza rejestru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `Read` sprawdza, czy `pszKey` jako podklucz `m_hKey`.  
  
##  <a name="write"></a>  CSettingsStore::Write  
 Zapisuje wartość rejestru w kluczu otwarte.  
  
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
 [in] `pszKey`  
 Wskaźnik do ciągu zawierającego nazwę wartość do ustawienia.  
  
 [in] `iVal`  
 Odwołanie do zmiennej liczba całkowita, która zawiera dane, które mają być przechowywane.  
  
 [in] `dwVal`  
 Odwołanie do zmiennej 32-bitowe o podwójnej precyzji word, która zawiera dane, które mają być przechowywane.  
  
 [in] `pszVal`  
 Wskaźnik do zmiennej ciągu zakończonego wartością null, która zawiera dane, które mają być przechowywane.  
  
 [in] `scStringList`  
 Odwołanie do [CStringList](../../mfc/reference/cstringlist-class.md) zmienna, która zawiera dane, które mają być przechowywane.  
  
 [in] `bcArray`  
 Odwołanie do zmiennej tablicy typu byte, która zawiera dane, które mają być przechowywane.  
  
 [in] `scArray`  
 Odwołanie do zmiennej tablicy ciągów, która zawiera dane, które mają być przechowywane.  
  
 [in] `dwcArray`  
 Odwołanie do zmiennej tablicy 32-bitowe o podwójnej precyzji word, która zawiera dane, które mają być przechowywane.  
  
 [in] `wcArray`  
 Odwołanie do zmiennej tablicy word 16-bitowego, która zawiera dane, które mają być przechowywane.  
  
 [in] `rect`  
 Odwołanie do [CRect](../../atl-mfc-shared/reference/crect-class.md) zmienna, która zawiera dane, które mają być przechowywane.  
  
 [in] `lpPoint`  
 Odwołanie do wskaźnika do `POINT` zmienna, która zawiera dane, które mają być przechowywane.  
  
 [in] `pData`  
 Wskaźnik do buforu, który zawiera dane, które mają być przechowywane.  
  
 [in] `nBytes`  
 Określa rozmiar w bajtach danych, do których `pData` punktów parametru.  
  
 [in] `list`  
 Odwołanie do [CObList](../../mfc/reference/coblist-class.md) zmienna, która zawiera dane, które mają być przechowywane.  
  
 [in] `obj`  
 Odwołanie do [CObject](../../mfc/reference/cobject-class.md) zmienna, która zawiera dane, które mają być przechowywane.  
  
 [in] `pObj`  
 Wskaźnik na wskaźnik do `CObject` zmienna, która zawiera dane, które mają być przechowywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` w przypadku powodzenia; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Aby można było zapisać w rejestrze, należy ustawić `bReadOnly` jako wartość niezerową, podczas tworzenia [CSettingsStore](../../mfc/reference/csettingsstore-class.md) obiektu. Aby uzyskać więcej informacji, zobacz [CSettingsStore::CSettingsStore](#csettingsstore).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)
