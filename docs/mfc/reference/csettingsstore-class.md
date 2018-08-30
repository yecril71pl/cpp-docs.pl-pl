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
ms.openlocfilehash: 1731c32506ec0e9c4c392ff9429e28e5b71b3c7c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221135"
---
# <a name="csettingsstore-class"></a>Klasa CSettingsStore
Opakowuje funkcje Windows API, zapewniając interfejs zorientowany obiektowo, który umożliwia dostępu do rejestru.  
  
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
|[CSettingsStore::CreateKey](#createkey)|Otwiera określony klucz lub go utworzy, jeśli nie istnieje.|  
|[CSettingsStore::DeleteKey](#deletekey)|Usuwa określony klucz i jego elementów podrzędnych.|  
|[CSettingsStore::DeleteValue](#deletevalue)|Usuwa określoną wartość otworzyć klucza.|  
|[CSettingsStore::Open](#open)|Otwiera określony klucz.|  
|[CSettingsStore::Read](#read)|Pobiera dane dla określoną wartością klucza.|  
|[CSettingsStore::Write](#write)|Zapisuje wartość rejestru w kluczu open.|  
  
## <a name="remarks"></a>Uwagi  
 Funkcje elementów członkowskich `CreateKey` i `Open` są bardzo podobne. Jeśli istnieje już klucz rejestru, `CreateKey` i `Open` funkcji w taki sam sposób. Jednakże, jeśli klucz rejestru nie istnieje, `CreateKey` zostanie ona utworzona, natomiast `Open` zwróci wartość błędu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób użycia metody Open i Odczyt `CSettingsStore` klasy. Ten fragment kodu jest częścią [próbka Demo Porada narzędzie](../../visual-cpp-samples.md).  
  
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
 Domyślnie ta metoda jest wywoływana z destruktora z [klasa CSettingsStore](../../mfc/reference/csettingsstore-class.md).  
  
##  <a name="createkey"></a>  CSettingsStore::CreateKey  
 Otwiera klucza rejestru lub go utworzy, jeśli nie istnieje.  
  
```  
virtual BOOL CreateKey(LPCTSTR pszPath);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pszPath*  
 Określa nazwę klucza, który ma zostać utworzony lub otwarty.  
  
### <a name="return-value"></a>Wartość zwracana  
 0 w przypadku powodzenia; w przeciwnym razie wartość różną od zera.  
  
### <a name="remarks"></a>Uwagi  
 `CreateKey` używa `m_hKey` jako katalogu głównego rejestru zapytania. Wyszukuje ona *pszPath* jako podklucz `m_hKey`. Jeśli klucz nie istnieje, `CreateKey` tworzy go. W przeciwnym razie zostanie otwarty klucza. `CreateKey` następnie ustawia `m_hKey` kluczowi utworzone lub otwarte.  
  
##  <a name="csettingsstore"></a>  CSettingsStore::CSettingsStore  
 Tworzy `CSettngsStore` obiektu.  
  
```  
CSettingsStore(
    BOOL bAdmin,  
    BOOL bReadOnly);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bŚcieżka*  
 Parametr logiczny, który określa, czy `CSettingsStore` obiektu działa w trybie administratora.  
  
 [in] *bReadOnly*  
 Parametr logiczny, który określa, czy `CSettingsStore` obiekt zostanie utworzony w trybie tylko do odczytu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *bŚcieżka* jest ustawiona na wartość TRUE, `m_hKey` element członkowski, zmienna jest ustawiona na **HKEY_LOCAL_MACHINE**. Jeśli ustawisz *bŚcieżka* na wartość FALSE, `m_hKey` ustawiono **HKEY_CURRENT_USER**.  
  
 Zabezpieczenia dostępu jest zależna od *bReadOnly* parametru. Jeśli *bReadonly* ma wartość FALSE, zostaną ustawione zabezpieczenia dostępu **KEY_ALL_ACCESS**. Jeśli *bReadyOnly* ma wartość PRAWDA, zabezpieczenia dostępu zostaną ustawione kombinacji **KEY_QUERY_VALUE, KEY_NOTIFY** i **KEY_ENUMERATE_SUB_KEYS**. Aby uzyskać więcej informacji na temat dostępu zabezpieczeń wraz z rejestru, zobacz [zabezpieczeń klucza rejestru i prawa dostępu](/windows/desktop/SysInfo/registry-key-security-and-access-rights).  
  
 Destruktor dla `CSettingsStore` zwalnia `m_hKey` automatycznie.  
  
##  <a name="deletekey"></a>  CSettingsStore::DeleteKey  
 Usuwa klucz i wszystkich jego obiektów podrzędnych z rejestru.  
  
```  
virtual BOOL DeleteKey(
    LPCTSTR pszPath,  
    BOOL bAdmin = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pszPath*  
 Nazwa klucza do usunięcia.  
  
 [in] *bŚcieżka*  
 Przełącznik, który określa lokalizację klucza do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zakończy się niepowodzeniem, jeśli `CSettingsStore` obiekt jest w trybie tylko do odczytu.  
  
 Jeśli parametr *bŚcieżka* wynosi zero, `DeleteKey` wyszukuje klucz do usunięcia w ramach **HKEY_CURRENT_USER**. Jeśli *bŚcieżka* jest różna od zera, `DeleteKey` wyszukuje klucz do usunięcia w ramach **HKEY_LOCAL_MACHINE**.  
  
##  <a name="deletevalue"></a>  CSettingsStore::DeleteValue  
 Usuwa wartość z zakresu od `m_hKey`.  
  
```  
virtual BOOL DeleteValue(LPCTSTR pszValue);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pszValue*  
 Określa pole wartości do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
##  <a name="open"></a>  CSettingsStore::Open  
 Zostanie otwarty klucza rejestru.  
  
```  
virtual BOOL Open(LPCTSTR pszPath);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pszPath*  
 Nazwa klucza rejestru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Po tej metody pomyślnie otwiera określony klucz, ustawia `m_hKey` obsługiwać tego klucza.  
  
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
 [in] *pszKey*  
 Wskaźnik na ciąg zakończony znakiem null, zawierającego nazwę wartości, które można odczytać z rejestru.  
  
 [out] *iVal*  
 Odwołanie do zmiennej całkowitej, który odbiera wartość odczytu z klucza rejestru.  
  
 [out] *dwVal*  
 Odwołanie do zmiennej 32-bitowych podwójne słowo, który odbiera wartość odczytu z klucza rejestru.  
  
 [out] *sVal*  
 Odwołanie do zmiennej ciągu, który odbiera wartość odczytu z klucza rejestru.  
  
 [out] *scStringList*  
 Odwołanie do zmiennej listy ciągu, który odbiera wartość odczytu z klucza rejestru.  
  
 [out] *scArray*  
 Odwołanie do zmiennej tablicowej ciąg, który odbiera wartość odczytu z klucza rejestru.  
  
 [out] *dwcArray*  
 Odwołanie do zmiennej tablicowej 32-bitowych podwójne słowo, który odbiera wartość odczytu z klucza rejestru.  
  
 [out] *wcArray*  
 Odwołanie do zmiennej tablicowej 16-bitowe słowo, który odbiera wartość odczytu z klucza rejestru.  
  
 [out] *bcArray*  
 Odwołanie do zmiennej tablicy bajtów, który odbiera wartość odczytu z klucza rejestru.  
  
 [out] *lppoint —*  
 Odwołanie do wskaźnika do `POINT` strukturę, która otrzymuje wartość odczytu z klucza rejestru.  
  
 [out] *rect*  
 Odwołanie do [CRect](../../atl-mfc-shared/reference/crect-class.md) zmiennej, która otrzymuje wartość odczytu z klucza rejestru.  
  
 [out] *ppData*  
 Wskaźnik do wskaźnika do danych, który odbiera wartość odczytu z klucza rejestru.  
  
 [out] *pBytes*  
 Wskaźnik do zmiennej liczby całkowitej bez znaku. Zmienna ta otrzymuje rozmiar buforu, który *ppData* wskazuje.  
  
 [out] *listy*  
 Odwołanie do [CObList](../../mfc/reference/coblist-class.md) zmiennej, która otrzymuje wartość odczytu z klucza rejestru.  
  
 [out] *obj*  
 Odwołanie do [CObject](../../mfc/reference/cobject-class.md) zmiennej, która otrzymuje wartość odczytu z klucza rejestru.  
  
 [out] *pObj*  
 Odwołanie do wskaźnika do `CObject` zmiennej, która otrzymuje wartość odczytu z klucza rejestru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `Read` sprawdza, czy *pszKey* jako podklucz `m_hKey`.  
  
##  <a name="write"></a>  CSettingsStore::Write  
 Zapisuje wartość rejestru w kluczu open.  
  
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
 [in] *pszKey*  
 Wskaźnik do ciągu, który zawiera nazwę wartość do ustawienia.  
  
 [in] *iVal*  
 Odwołanie do zmiennej całkowitej, która zawiera dane, które mają być przechowywane.  
  
 [in] *dwVal*  
 Odwołanie do zmiennej 32-bitowych podwójne słowo, która zawiera dane, które mają być przechowywane.  
  
 [in] *pszVal*  
 Wskaźnik do zmiennej ciągu zakończonego znakiem null, która zawiera dane, które mają być przechowywane.  
  
 [in] *scStringList*  
 Odwołanie do [CStringList](../../mfc/reference/cstringlist-class.md) zmiennej, która zawiera dane, które mają być przechowywane.  
  
 [in] *bcArray*  
 Odwołanie do zmiennej tablicy bajtów, która zawiera dane, które mają być przechowywane.  
  
 [in] *scArray*  
 Odwołanie do zmiennej tablicowej ciąg, który zawiera dane, które mają być przechowywane.  
  
 [in] *dwcArray*  
 Odwołanie do zmiennej tablicowej 32-bitowych podwójne słowo, który zawiera dane, które mają być przechowywane.  
  
 [in] *wcArray*  
 Odwołanie do zmiennej tablicowej 16-bitowe słowo, który zawiera dane, które mają być przechowywane.  
  
 [in] *rect*  
 Odwołanie do [CRect](../../atl-mfc-shared/reference/crect-class.md) zmiennej, która zawiera dane, które mają być przechowywane.  
  
 [in] *lppoint —*  
 Odwołanie do wskaźnika do `POINT` zmiennej, która zawiera dane, które mają być przechowywane.  
  
 [in] *pData*  
 Wskaźnik do buforu, który zawiera dane, które mają być przechowywane.  
  
 [in] *nBytes*  
 Określa rozmiar w bajtach, danych, do których *pData* punktów parametru.  
  
 [in] *listy*  
 Odwołanie do [CObList](../../mfc/reference/coblist-class.md) zmiennej, która zawiera dane, które mają być przechowywane.  
  
 [in] *obj*  
 Odwołanie do [CObject](../../mfc/reference/cobject-class.md) zmiennej, która zawiera dane, które mają być przechowywane.  
  
 [in] *pObj*  
 Wskaźnik do wskaźnika do `CObject` zmiennej, która zawiera dane, które mają być przechowywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli to się powiedzie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Aby można było zapisać do rejestru, należy ustawić *bReadOnly* na wartość różną od zera, tworząc [CSettingsStore](../../mfc/reference/csettingsstore-class.md) obiektu. Aby uzyskać więcej informacji, zobacz [CSettingsStore::CSettingsStore](#csettingsstore).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)
