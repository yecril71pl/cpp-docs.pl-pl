---
title: Klasa CPictureHolder | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPictureHolder
- AFXCTL/CPictureHolder
- AFXCTL/CPictureHolder::CPictureHolder
- AFXCTL/CPictureHolder::CreateEmpty
- AFXCTL/CPictureHolder::CreateFromBitmap
- AFXCTL/CPictureHolder::CreateFromIcon
- AFXCTL/CPictureHolder::CreateFromMetafile
- AFXCTL/CPictureHolder::GetDisplayString
- AFXCTL/CPictureHolder::GetPictureDispatch
- AFXCTL/CPictureHolder::GetType
- AFXCTL/CPictureHolder::Render
- AFXCTL/CPictureHolder::SetPictureDispatch
- AFXCTL/CPictureHolder::m_pPict
dev_langs:
- C++
helpviewer_keywords:
- CPictureHolder [MFC], CPictureHolder
- CPictureHolder [MFC], CreateEmpty
- CPictureHolder [MFC], CreateFromBitmap
- CPictureHolder [MFC], CreateFromIcon
- CPictureHolder [MFC], CreateFromMetafile
- CPictureHolder [MFC], GetDisplayString
- CPictureHolder [MFC], GetPictureDispatch
- CPictureHolder [MFC], GetType
- CPictureHolder [MFC], Render
- CPictureHolder [MFC], SetPictureDispatch
- CPictureHolder [MFC], m_pPict
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 90bc58ce3d56852b983a673968df97b55f4bdeab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cpictureholder-class"></a>Klasa CPictureHolder
Implementuje właściwości obrazu, dzięki czemu użytkownika wyświetlić obraz w formantu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CPictureHolder  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPictureHolder::CPictureHolder](#cpictureholder)|Konstruuje `CPictureHolder` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPictureHolder::CreateEmpty](#createempty)|Tworzy pustą `CPictureHolder` obiektu.|  
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|Tworzy `CPictureHolder` obiektu z mapy bitowej.|  
|[CPictureHolder::CreateFromIcon](#createfromicon)|Tworzy `CPictureHolder` obiektu z ikony.|  
|[CPictureHolder::CreateFromMetafile](#createfrommetafile)|Tworzy `CPictureHolder` obiektu metaplik.|  
|[CPictureHolder::GetDisplayString](#getdisplaystring)|Pobiera ciąg wyświetlany w przeglądarce właściwości formantu kontenera.|  
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|Zwraca `CPictureHolder` obiektu `IDispatch` interfejsu.|  
|[CPictureHolder::GetType](#gettype)|Informuje, czy `CPictureHolder` obiekt jest mapą bitową, metaplików lub ikony.|  
|[CPictureHolder::Render](#render)|Renderuje obraz.|  
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|Ustawia `CPictureHolder` obiektu `IDispatch` interfejsu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPictureHolder::m_pPict](#m_ppict)|Wskaźnik do obiektu obrazu.|  
  
## <a name="remarks"></a>Uwagi  
 `CPictureHolder`nie ma klasy podstawowej.  
  
 Razem z właściwością obrazu podstawowego dewelopera można określić mapy bitowej, ikona lub metaplik do wyświetlenia.  
  
 Informacje dotyczące tworzenia właściwości niestandardowego obrazu, zobacz artykuł [kontrolki ActiveX MFC: Korzystanie z obrazów w formancie ActiveX](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CPictureHolder`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxctl.h  
  
##  <a name="cpictureholder"></a>CPictureHolder::CPictureHolder  
 Konstruuje `CPictureHolder` obiektu.  
  
```  
CPictureHolder();
```  
  
##  <a name="createempty"></a>CPictureHolder::CreateEmpty  
 Tworzy pustą `CPictureHolder` obiektu i łączy go do `IPicture` interfejsu.  
  
```  
BOOL CreateEmpty();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obiekt jest pomyślnie utworzony; w przeciwnym razie 0.  
  
##  <a name="createfrombitmap"></a>CPictureHolder::CreateFromBitmap  
 Używa mapy bitowej do zainicjowania obiektu obrazu w `CPictureHolder`.  
  
```  
BOOL CreateFromBitmap(
    UINT idResource);

 
BOOL CreateFromBitmap(
    CBitmap* pBitmap,  
    CPalette* pPal = NULL,  
    BOOL bTransferOwnership = TRUE);

 
BOOL CreateFromBitmap(
    HBITMAP hbm,  
    HPALETTE hpal = NULL,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `idResource`  
 Identyfikator zasobu zasobu mapy bitowej.  
  
 `pBitmap`  
 Wskaźnik do [cbitmap —](../../mfc/reference/cbitmap-class.md) obiektu.  
  
 *pPal*  
 Wskaźnik do [cpalette —](../../mfc/reference/cpalette-class.md) obiektu.  
  
 `bTransferOwnership`  
 Wskazuje, czy obiekt obrazu będzie przejąć na własność obiekt mapy bitowej i palety.  
  
 `hbm`  
 Dojście do mapy bitowej, z którego `CPictureHolder` tworzony jest obiekt.  
  
 `hpal`  
 Dojście do palety używany do renderowania mapy bitowej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obiekt jest pomyślnie utworzony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bTransferOwnership` jest **TRUE**, obiekt wywołujący nie należy używać mapy bitowej lub zwraca obiekt palety w jakikolwiek sposób po tym wywołaniu. Jeśli `bTransferOwnership` jest **FALSE**, element wywołujący jest odpowiedzialny za zapewnienie, że obiekt mapy bitowej i palety pozostają w mocy okres istnienia obiektu obrazu.  
  
##  <a name="createfromicon"></a>CPictureHolder::CreateFromIcon  
 Używa ikonę można zainicjować obiektu obrazu w `CPictureHolder`.  
  
```  
BOOL CreateFromIcon(
    UINT idResource);

 
BOOL CreateFromIcon(
    HICON hIcon,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `idResource`  
 Identyfikator zasobu zasobu mapy bitowej.  
  
 `hIcon`  
 Dojście do ikony, z którego `CPictureHolder` tworzony jest obiekt.  
  
 `bTransferOwnership`  
 Wskazuje, czy obiekt obrazu będzie przejąć na własność obiekt ikony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obiekt jest pomyślnie utworzony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bTransferOwnership` jest **TRUE**, obiekt wywołujący nie należy używać obiekt ikony w jakikolwiek sposób po powrocie tego wywołania. Jeśli `bTransferOwnership` jest **FALSE**, element wywołujący jest odpowiedzialny za egzekwowanie obiekt ikony pozostaje ważny przez czas ich istnienia obiektu obrazu.  
  
##  <a name="createfrommetafile"></a>CPictureHolder::CreateFromMetafile  
 Używa metaplik można zainicjować obiektu obrazu w `CPictureHolder`.  
  
```  
BOOL CreateFromMetafile(
    HMETAFILE hmf,  
    int xExt,  
    int yExt,  
    BOOL bTransferOwnership = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `hmf`  
 Dojście do metaplik użyty do utworzenia `CPictureHolder` obiektu.  
  
 *xExt*  
 X zakres obrazu.  
  
 *yExt*  
 Zakres Y obrazu.  
  
 `bTransferOwnership`  
 Wskazuje, czy obiekt obrazu będzie przejąć prawo własności obiektu metaplik.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obiekt jest pomyślnie utworzony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bTransferOwnership` jest **TRUE**, obiekt wywołujący nie należy używać obiektu metaplik w jakikolwiek sposób po powrocie tego wywołania. Jeśli `bTransferOwnership` jest **FALSE**, element wywołujący jest odpowiedzialny za egzekwowanie obiektu metaplik pozostaje ważny przez czas ich istnienia obiektu obrazu.  
  
##  <a name="getdisplaystring"></a>CPictureHolder::GetDisplayString  
 Pobiera ciąg, który jest wyświetlany w przeglądarce właściwości kontenera.  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>Parametry  
 `strValue`  
 Odwołanie do [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) do przechowywania ciągu wyświetlanego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ciąg jest pomyślnie pobrać; w przeciwnym razie 0.  
  
##  <a name="getpicturedispatch"></a>CPictureHolder::GetPictureDispatch  
 Ta funkcja zwraca wskaźnik do `CPictureHolder` obiektu `IPictureDisp` interfejsu.  
  
```  
LPPICTUREDISP GetPictureDispatch();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CPictureHolder` obiektu `IPictureDisp` interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt wywołujący musi wywołać **wersji** na ten wskaźnik po jej zakończeniu.  
  
##  <a name="gettype"></a>CPictureHolder::GetType  
 Wskazuje, czy obraz mapy bitowej, metaplik lub ikonę.  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość wskazująca typ obrazu. Możliwe wartości i ich znaczenie są następujące:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|**PICTYPE_UNINITIALIZED**|`CPictureHolder`obiekt jest unititialized.|  
|**PICTYPE_NONE**|`CPictureHolder`obiekt jest pusty.|  
|**PICTYPE_BITMAP**|Obraz jest mapą bitową.|  
|**PICTYPE_METAFILE**|Obraz jest metaplik.|  
|**PICTYPE_ICON**|Obraz jest ikona.|  
  
##  <a name="m_ppict"></a>CPictureHolder::m_pPict  
 Wskaźnik do `CPictureHolder` obiektu `IPicture` interfejsu.  
  
```  
LPPICTURE m_pPict;  
```  
  
##  <a name="render"></a>CPictureHolder::Render  
 Renderuje obraz w prostokącie odwołuje się `rcRender`.  
  
```  
void Render(
    CDC* pDC,  
    const CRect& rcRender,  
    const CRect& rcWBounds);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskaźnik do kontekstu wyświetlania, w którym ma być renderowany obraz.  
  
 `rcRender`  
 Prostokąt, w którym ma być renderowany obraz.  
  
 *rcWBounds*  
 Prostokąt reprezentujący prostokątem obiektu renderowania obrazu. W przypadku formantu tym prostokącie, gdzie jest `rcBounds` parametr przekazany do zastępowania [COleControl::OnDraw](../../mfc/reference/colecontrol-class.md#ondraw).  
  
##  <a name="setpicturedispatch"></a>CPictureHolder::SetPictureDispatch  
 Łączy `CPictureHolder` do obiektu `IPictureDisp` interfejsu.  
  
```  
void SetPictureDispatch(LPPICTUREDISP pDisp);
```  
  
### <a name="parameters"></a>Parametry  
 `pDisp`  
 Wskaźnik do nowego `IPictureDisp` interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CFontHolder](../../mfc/reference/cfontholder-class.md)
