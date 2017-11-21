---
title: Klasa CFontHolder | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFontHolder
- AFXCTL/CFontHolder
- AFXCTL/CFontHolder::CFontHolder
- AFXCTL/CFontHolder::GetDisplayString
- AFXCTL/CFontHolder::GetFontDispatch
- AFXCTL/CFontHolder::GetFontHandle
- AFXCTL/CFontHolder::InitializeFont
- AFXCTL/CFontHolder::QueryTextMetrics
- AFXCTL/CFontHolder::ReleaseFont
- AFXCTL/CFontHolder::Select
- AFXCTL/CFontHolder::SetFont
- AFXCTL/CFontHolder::m_pFont
dev_langs: C++
helpviewer_keywords:
- CFontHolder [MFC], CFontHolder
- CFontHolder [MFC], GetDisplayString
- CFontHolder [MFC], GetFontDispatch
- CFontHolder [MFC], GetFontHandle
- CFontHolder [MFC], InitializeFont
- CFontHolder [MFC], QueryTextMetrics
- CFontHolder [MFC], ReleaseFont
- CFontHolder [MFC], Select
- CFontHolder [MFC], SetFont
- CFontHolder [MFC], m_pFont
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b7561c9765dcbead36335852d457568bd76b46e5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cfontholder-class"></a>Klasa CFontHolder
Implementuje standardowych właściwość czcionki i hermetyzuje funkcjonalność obiektu czcionki systemu Windows i `IFont` interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CFontHolder  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFontHolder::CFontHolder](#cfontholder)|Konstruuje `CFontHolder` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFontHolder::GetDisplayString](#getdisplaystring)|Pobiera ciąg wyświetlany w przeglądarce właściwości kontenera.|  
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Zwraca czcionki `IDispatch` interfejsu.|  
|[CFontHolder::GetFontHandle](#getfonthandle)|Zwraca dojście do czcionki systemu Windows.|  
|[CFontHolder::InitializeFont](#initializefont)|Inicjuje `CFontHolder` obiektu.|  
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Pobiera informacje o powiązanych czcionki.|  
|[CFontHolder::ReleaseFont](#releasefont)|Odłącza `CFontHolder` obiekt z `IFont` i `IFontNotification` interfejsów.|  
|[CFontHolder::Select](#select)|Wybiera czcionkę zasobu do kontekstu urządzenia.|  
|[CFontHolder::SetFont](#setfont)|Łączy `CFontHolder` do obiektu `IFont` interfejsu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFontHolder::m_pFont](#m_pfont)|Wskaźnik do `CFontHolder` obiektu `IFont` interfejsu.|  
  
## <a name="remarks"></a>Uwagi  
 `CFontHolder`nie ma klasy podstawowej.  
  
 Ta klasa umożliwia Implementowanie właściwości niestandardowe czcionki dla formantu. Informacje o tworzeniu takich właściwości, zobacz artykuł [formantów ActiveX: przy użyciu czcionek](../../mfc/mfc-activex-controls-using-fonts.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CFontHolder`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxctl.h  
  
##  <a name="cfontholder"></a>CFontHolder::CFontHolder  
 Konstruuje `CFontHolder` obiektu.  
  
```  
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```  
  
### <a name="parameters"></a>Parametry  
 *pNotify*  
 Wskaźnik do czcionki `IPropertyNotifySink` interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać `InitializeFont` zainicjować wynikowy obiekt przed jego użyciem.  
  
##  <a name="getdisplaystring"></a>CFontHolder::GetDisplayString  
 Pobiera ciąg, który może być wyświetlany w przeglądarce właściwości kontenera.  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>Parametry  
 `strValue`  
 Odwołanie do [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) do przechowywania ciągu wyświetlanego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ciąg jest pomyślnie pobrać; w przeciwnym razie 0.  
  
##  <a name="getfontdispatch"></a>CFontHolder::GetFontDispatch  
 Wywołanie tej funkcji można pobrać wskaźnik do interfejsu wysyłania czcionki.  
  
```  
LPFONTDISP GetFontDispatch();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CFontHolder` obiektu **IFontDisp** interfejsu. Należy pamiętać, że funkcja wywołującym `GetFontDispatch` należy wywołać `IUnknown::Release` na ten wskaźnik interfejsu po zakończeniu z nim.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie `InitializeFont` przed wywołaniem `GetFontDispatch`.  
  
##  <a name="getfonthandle"></a>CFontHolder::GetFontHandle  
 Wywołanie tej funkcji można uzyskać dojścia do czcionki systemu Windows.  
  
```  
HFONT GetFontHandle();

 
HFONT GetFontHandle(
    long cyLogical,  
    long cyHimetric);
```  
  
### <a name="parameters"></a>Parametry  
 `cyLogical`  
 Wysokość w jednostkach logicznych, prostokąt, w którym zostanie narysowana formantu.  
  
 `cyHimetric`  
 Wysokość w `MM_HIMETRIC` jednostki formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do obiektu czcionki. w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Stosunek `cyLogical` i `cyHimetric` służy do obliczania rozmiaru prawidłowego wyświetlania, w jednostkach logicznych, rozmiar czcionki w punktach wyrażone w `MM_HIMETRIC` jednostki:  
  
 Format wyświetlania = ( `cyLogical`  /  `cyHimetric`) X rozmiar czcionki  
  
 Wersja bez parametrów zwraca uchwyt do czcionki mały rozmiar dla ekranu.  
  
##  <a name="initializefont"></a>CFontHolder::InitializeFont  
 Inicjuje `CFontHolder` obiektu.  
  
```  
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,  
    LPDISPATCH pFontDispAmbient = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pFontDesc`  
 Wskaźnik do struktury opis czcionek ( [FONTDESC](http://msdn.microsoft.com/library/windows/desktop/ms692782)), który określa właściwości czcionki.  
  
 `pFontDispAmbient`  
 Wskaźnik do kontenera otoczenia właściwość czcionki.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `pFontDispAmbient` nie jest **NULL**, `CFontHolder` obiekt jest połączony z klonu `IFont` interfejs używany przez właściwość czcionki otoczenia kontenera.  
  
 Jeśli `pFontDispAmbient` jest **NULL**, tworzony jest nowy obiekt czcionki, albo z opisu czcionki wskazywana przez `pFontDesc` lub, jeśli `pFontDesc` jest **NULL**, z domyślny opis.  
  
 Wywołanie tej funkcji po konstruowania `CFontHolder` obiektu.  
  
##  <a name="m_pfont"></a>CFontHolder::m_pFont  
 Wskaźnik do `CFontHolder` obiektu `IFont` interfejsu.  
  
```  
LPFONT m_pFont;  
```  
  
##  <a name="querytextmetrics"></a>CFontHolder::QueryTextMetrics  
 Pobiera informacje o fizycznej czcionki reprezentowany przez `CFontHolder` obiektu.  
  
```  
void QueryTextMetrics(LPTEXTMETRIC lptm);
```  
  
### <a name="parameters"></a>Parametry  
 `lptm`  
 Wskaźnik do [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) strukturę, która będzie odbierać dane.  
  
##  <a name="releasefont"></a>CFontHolder::ReleaseFont  
 Ta funkcja rozłącza `CFontHolder` obiekt z jego `IFont` interfejsu.  
  
```  
void ReleaseFont();
```  
  
##  <a name="select"></a>CFontHolder::Select  
 Wywołanie tej funkcji, aby wybrać czcionki formantu w kontekście określonego urządzenia.  
  
```  
CFont* Select(
    CDC* pDC,  
    long cyLogical,  
    long cyHimetric);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Kontekst urządzenia, do którego wybrano czcionki.  
  
 `cyLogical`  
 Wysokość w jednostkach logicznych, prostokąt, w którym zostanie narysowana formantu.  
  
 `cyHimetric`  
 Wysokość w `MM_HIMETRIC` jednostki formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do czcionki, który jest zastępowany.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [GetFontHandle](#getfonthandle) omówienie `cyLogical` i `cyHimetric` parametrów.  
  
##  <a name="setfont"></a>CFontHolder::SetFont  
 Zwalnia wszelkie istniejące czcionki i łączy `CFontHolder` do obiektu `IFont` interfejsu.  
  
```  
void SetFont(LPFONT pNewFont);
```  
  
### <a name="parameters"></a>Parametry  
 *pNewFont*  
 Wskaźnik do nowego `IFont` interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CPropExchange](../../mfc/reference/cpropexchange-class.md)
