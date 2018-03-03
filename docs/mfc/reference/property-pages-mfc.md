---
title: "Strony właściwości (MFC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e53260457470ef75ac706779cea323aa5b73da2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="property-pages-mfc"></a>Strony właściwości (MFC)
Strony właściwości Wyświetl bieżące wartości właściwości specyficzne dla formantu OLE w można dostosowywać, interfejs graficzny służący do wyświetlania i edytowania dzięki obsłudze mechanizm mapowanie danych oparte na wymiana danych okna dialogowego (DDX).  
  
 Ten mechanizm mapowanie danych mapy formantów strony właściwości do poszczególnych właściwości formantu OLE. Wartość właściwości formantu odzwierciedla stan lub zawartości formantu strony właściwości. Mapowanie między formantów strony właściwości i właściwości jest określona przez **ddp_ —** wywołania funkcji na stronie właściwości `DoDataExchange` funkcję elementu członkowskiego. Poniżej przedstawiono listę **ddp_ —** funkcje, które wymieniać dane wprowadzane przy użyciu strony właściwości formantu:  
  
### <a name="property-page-data-transfer"></a>Transfer danych strony właściwości  
  
|||  
|-|-|  
|[Ddp_cbindex —](#ddp_cbindex)|Łączy zaznaczony ciąg indeksu w polu kombi z właściwością formantu.|  
|[Ddp_cbstring —](#ddp_cbstring)|Łączy zaznaczony ciąg w polu kombi z właściwością formantu. Zaznaczony ciąg może rozpoczynać się od tych samych liter jako wartość właściwości, ale nie musi być zgodny go całkowicie.|  
|[Ddp_cbstringexact —](#ddp_cbstringexact)|Łączy zaznaczony ciąg w polu kombi z właściwością formantu. Zaznaczony ciąg i wartość ciągu właściwości muszą być całkowicie zgodne.|  
|[Ddp_check —](#ddp_check)|Łącza pola wyboru na stronie właściwości formantu za pomocą właściwości formantu.|  
|[Ddp_lbindex —](#ddp_lbindex)|Łączy zaznaczony ciąg indeksu w polu listy z właściwością formantu.|  
|[Ddp_lbstring —](#ddp_lbstring)|Łączy zaznaczony ciąg w polu listy z właściwością formantu. Zaznaczony ciąg może rozpoczynać się od tych samych liter jako wartość właściwości, ale nie musi być zgodne go całkowicie.|  
|[Ddp_lbstringexact —](#ddp_lbstringexact)|Łączy zaznaczony ciąg w polu listy z właściwością formantu. Zaznaczony ciąg i wartość ciągu właściwości muszą być całkowicie zgodne.|  
|[Ddp_postprocessing —](#ddp_postprocessing)|Zakończeniu transferu wartości właściwości z formantu.|  
|[Ddp_radio —](#ddp_radio)|Grupa przycisków radiowych, na stronie właściwości formantu za pomocą właściwości formantu łącza.|  
|[Ddp_text —](#ddp_text)|Łącza kontrolki na stronie właściwości formantu za pomocą właściwości formantu. Ta funkcja obsługuje kilka różnych typów właściwości, takie jak **podwójne**, **krótki**, `BSTR`, i **długi**.|  
  
 Aby uzyskać więcej informacji na temat `DoDataExchange` funkcji i właściwości strony, zobacz artykuł [formantów ActiveX: strony właściwości](../../mfc/mfc-activex-controls-property-pages.md).  
  
 Poniżej przedstawiono listę makra używane do tworzenia i zarządzania nimi strony właściwości dla formantu OLE:  
  
### <a name="property-pages"></a>Strony właściwości  
  
|||  
|-|-|  
|[BEGIN_PROPPAGEIDS —](#begin_proppageids)|Rozpoczyna się na liście identyfikatorów stron właściwości.|  
|[END_PROPPAGEIDS —](#end_proppageids)|Kończy się na liście identyfikatorów stron właściwości.|  
|[PROPPAGEID —](#proppageid)|Deklaruje strony właściwości klasy formantu.|  
  
##  <a name="ddp_cbindex"></a>Ddp_cbindex —  
 Wywołanie tej funkcji na stronie właściwości `DoDataExchange` funkcja synchronizacji wartość właściwości Liczba całkowita z indeksem bieżące zaznaczenie w polu kombi na stronie właściwości.  
  
```   
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,  
    int id,  
    int& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `id`  
 Identyfikator zasobu pole kombi polu formantu skojarzony z określonym przez właściwość kontrolki `pszPropName`.  
  
 `member`  
 Zmiennej członkowskiej skojarzony z formantem strony właściwości określone przez `id` i określona przez właściwość `pszPropName`.  
  
 `pszPropName`  
 Nazwa właściwości właściwość formantu wymienianych z kontrolki pola kombi, które są określone przez `id`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja powinna być wywoływana przed odpowiadającego `DDX_CBIndex` wywołania funkcji.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="ddp_cbstring"></a>Ddp_cbstring —  
 Wywołanie tej funkcji na stronie właściwości `DoDataExchange` funkcja synchronizacji wartości właściwości ciągu z bieżącego zaznaczenia w polu kombi na stronie właściwości.  
  
```  
void AFXAPI DDP_CBString(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `id`  
 Identyfikator zasobu pole kombi polu formantu skojarzony z określonym przez właściwość kontrolki `pszPropName`.  
  
 `member`  
 Zmiennej członkowskiej skojarzony z formantem strony właściwości określone przez `id` i określona przez właściwość `pszPropName`.  
  
 `pszPropName`  
 Nazwa właściwości właściwość formantu wymienianych z określonej przez ciąg pole kombi `id`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja powinna być wywoływana przed odpowiadającego `DDX_CBString` wywołania funkcji.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="ddp_cbstringexact"></a>Ddp_cbstringexact —  
 Wywołanie tej funkcji na stronie właściwości `DoDataExchange` funkcji, aby zsynchronizować wartości właściwości ciągu, która dokładnie odpowiada bieżące zaznaczenie w polu kombi na stronie właściwości.  
  
```  
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `id`  
 Identyfikator zasobu pole kombi polu formantu skojarzony z określonym przez właściwość kontrolki `pszPropName`.  
  
 `member`  
 Zmiennej członkowskiej skojarzony z formantem strony właściwości określone przez `id` i określona przez właściwość `pszPropName`.  
  
 `pszPropName`  
 Nazwa właściwości właściwość formantu wymienianych z określonej przez ciąg pole kombi `id`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja powinna być wywoływana przed odpowiadającego `DDX_CBStringExact` wywołania funkcji.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="ddp_check"></a>Ddp_check —  
 Wywołanie tej funkcji na stronie właściwości `DoDataExchange` funkcja synchronizacji wartości właściwości z kontrolkę pola wyboru skojarzonej właściwości strony.  
  
```   
void AFXAPI DDP_Check(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `id`  
 Identyfikator zasobu kontrolkę pola wyboru skojarzone z określonym przez właściwość kontrolki `pszPropName`.  
  
 `member`  
 Zmiennej członkowskiej skojarzony z formantem strony właściwości określone przez `id` i określona przez właściwość `pszPropName`.  
  
 `pszPropName`  
 Nazwa właściwości właściwość formantu wymienianych z określonym przez kontrolkę pola wyboru `id`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja powinna być wywoływana przed odpowiadającego `DDX_Check` wywołania funkcji.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="ddp_lbindex"></a>Ddp_lbindex —  
 Wywołanie tej funkcji na stronie właściwości `DoDataExchange` funkcja synchronizacji wartość właściwości Liczba całkowita z indeksem bieżące zaznaczenie w polu listy na stronie właściwości.  
  
```   
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,  
    int id,  
    int& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `id`  
 Identyfikator zasobu listy polu formantu skojarzony z określonym przez właściwość kontrolki `pszPropName`.  
  
 `member`  
 Zmiennej członkowskiej skojarzony z formantem strony właściwości określone przez `id` i określona przez właściwość `pszPropName`.  
  
 `pszPropName`  
 Nazwa właściwości właściwość formantu wymienianych z określonej przez ciąg pole listy `id`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja powinna być wywoływana przed odpowiadającego `DDX_LBIndex` wywołania funkcji.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="ddp_lbstring"></a>Ddp_lbstring —  
 Wywołanie tej funkcji na stronie właściwości `DoDataExchange` funkcja synchronizacji wartości właściwości ciągu z bieżące zaznaczenie w polu listy na stronie właściwości.  
  
```   
void AFXAPI DDP_LBString(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `id`  
 Identyfikator zasobu listy polu formantu skojarzony z określonym przez właściwość kontrolki `pszPropName`.  
  
 `member`  
 Zmiennej członkowskiej skojarzony z formantem strony właściwości określone przez `id` i określona przez właściwość `pszPropName`.  
  
 `pszPropName`  
 Nazwa właściwości właściwość formantu wymienianych z określonej przez ciąg pole listy `id`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja powinna być wywoływana przed odpowiadającego `DDX_LBString` wywołania funkcji.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="ddp_lbstringexact"></a>Ddp_lbstringexact —  
 Wywołanie tej funkcji na stronie właściwości `DoDataExchange` funkcji, aby zsynchronizować wartości właściwości ciągu, która dokładnie odpowiada bieżące zaznaczenie w polu listy na stronie właściwości.  
  
```   
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `id`  
 Identyfikator zasobu listy polu formantu skojarzony z określonym przez właściwość kontrolki `pszPropName`.  
  
 `member`  
 Zmiennej członkowskiej skojarzony z formantem strony właściwości określone przez `id` i określona przez właściwość `pszPropName`.  
  
 `pszPropName`  
 Nazwa właściwości właściwość formantu wymienianych z określonej przez ciąg pole listy `id`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja powinna być wywoływana przed odpowiadającego `DDX_LBStringExact` wywołania funkcji.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="ddp_postprocessing"></a>Ddp_postprocessing —  
 Wywołanie tej funkcji na stronie właściwości `DoDataExchange` funkcji, aby zakończyć transferu wartości właściwości na stronie właściwości formantu po wartości właściwości są zapisywane.  
  
```   
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja powinna być wywoływana po ukończeniu wszystkich funkcje wymiany danych. Na przykład:  
  
 [!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="ddp_radio"></a>Ddp_radio —  
 Wywołanie tej funkcji w formantu `DoPropExchange` funkcja synchronizacji wartości właściwości z kontrolkę przycisku radiowego skojarzonej właściwości strony.  
  
```   
void AFXAPI DDP_Radio(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `id`  
 Formantu skojarzony z określonym przez właściwość kontrolki przycisku radiowego identyfikator zasobu `pszPropName`.  
  
 `member`  
 Zmiennej członkowskiej skojarzony z formantem strony właściwości określone przez `id` i określona przez właściwość `pszPropName`.  
  
 `pszPropName`  
 Nazwa właściwości właściwość formantu wymienianych z określonym przez kontrolkę przycisku radiowego `id`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja powinna być wywoływana przed odpowiadającego `DDX_Radio` wywołania funkcji.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="ddp_text"></a>Ddp_text —  
 Wywołanie tej funkcji w formantu `DoDataExchange` funkcja synchronizacji wartości właściwości z skojarzonej właściwości formantu strony.  
  
```   
void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    BYTE & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    UINT & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    long & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    DWORD & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    float & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    double & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    CString & member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Wskaźnik do `CDataExchange` obiektu. Platformę dostarcza tego obiektu w celu ustanowienia kontekście wymiany danych, w tym kierunku.  
  
 `id`  
 Identyfikator formantu skojarzony z określonym przez właściwość kontrolki zasobu `pszPropName`.  
  
 `member`  
 Zmiennej członkowskiej skojarzony z formantem strony właściwości określone przez `id` i określona przez właściwość `pszPropName`.  
  
 `pszPropName`  
 Nazwa właściwości właściwość formantu wymienianych z formantem określony przez `id`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja powinna być wywoływana przed odpowiadającego `DDX_Text` wywołania funkcji.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="begin_proppageids"></a>BEGIN_PROPPAGEIDS —  
 Rozpoczyna się definicji listy identyfikatorów stron właściwości formantu.  
  
```   
BEGIN_PROPPAGEIDS(class_name,  count)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Nazwa klasy formantu, dla którego właściwości są określone strony.  
  
 *Liczba*  
 Liczba stron właściwości używane przez klasy formantu.  
  
### <a name="remarks"></a>Uwagi  
 W pliku implementacji (.cpp), który definiuje funkcje Członkowskie dla klasy, należy uruchomić z listy stronę właściwości `BEGIN_PROPPAGEIDS` makra, Dodaj makro wpisy dla wszystkich stron właściwości i Pełna lista strony właściwości z `END_PROPPAGEIDS` makra.  
  
 Aby uzyskać więcej informacji na stronach właściwości, zobacz artykuł [formantów ActiveX: strony właściwości](../../mfc/mfc-activex-controls-property-pages.md).  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="end_proppageids"></a>END_PROPPAGEIDS —  
 Kończy definicję listy identyfikator strony właściwości.  
  
```   
END_PROPPAGEIDS(class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Nazwa klasy formantu, który jest właścicielem stronę właściwości.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="proppageid"></a>PROPPAGEID —  
 Dodaje strony właściwości do użycia przez formant OLE.  
  
```   
PROPPAGEID(clsid)   
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 Identyfikator unikatowy klasy strony właściwości.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie `PROPPAGEID` makra muszą znajdować się między `BEGIN_PROPPAGEIDS` i `END_PROPPAGEIDS` makra w pliku implementacji spod kontroli.  

### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
    
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
