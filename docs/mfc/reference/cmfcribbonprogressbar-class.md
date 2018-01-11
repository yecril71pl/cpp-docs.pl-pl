---
title: Klasa CMFCRibbonProgressBar | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMax
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMin
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRegularSize
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::IsInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::OnDraw
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetRange
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonProgressBar [MFC], CMFCRibbonProgressBar
- CMFCRibbonProgressBar [MFC], GetPos
- CMFCRibbonProgressBar [MFC], GetRangeMax
- CMFCRibbonProgressBar [MFC], GetRangeMin
- CMFCRibbonProgressBar [MFC], GetRegularSize
- CMFCRibbonProgressBar [MFC], IsInfiniteMode
- CMFCRibbonProgressBar [MFC], OnDraw
- CMFCRibbonProgressBar [MFC], SetInfiniteMode
- CMFCRibbonProgressBar [MFC], SetPos
- CMFCRibbonProgressBar [MFC], SetRange
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1354b0b15837a733a890c438c7771ffe39526773
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonprogressbar-class"></a>Klasa CMFCRibbonProgressBar
Implementuje formant, który wskazuje wizualnie postępu długotrwałej operacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](#cmfcribbonprogressbar)|Tworzy i inicjuje `CMFCRibbonProgressBar` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::GetPos](#getpos)|Zwraca bieżący postęp.|  
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|Zwraca maksymalną wartość bieżącego zakresu.|  
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|Zwraca minimalną wartość bieżącego zakresu.|  
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|Zwraca zwykłego rozmiaru elementu wstążki. (Przesłania [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|  
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|Określa, czy pasek postępu działa w trybie nieskończoną.|  
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|Wywoływane przez platformę, by narysować elementem wstążki. (Przesłania [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|  
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|Ustawia pasek postępu do pracy w trybie nieskończoną.|  
|[CMFCRibbonProgressBar::SetPos](#setpos)|Ustawia bieżący postęp.|  
|[CMFCRibbonProgressBar::SetRange](#setrange)|Ustawia wartości minimalną i maksymalną.|  
  
## <a name="remarks"></a>Uwagi  
 A `CMFCRibbonProgressBar` może działać w dwóch trybach: regularne i nieskończoną. W trybie regularne paska postępu jest wypełniany od lewej do prawej i zatrzymuje się wartość maksymalna. W trybie nieskończone paska postępu jest wielokrotnie wypełnione z wartością minimalną wartość maksymalna. Można użyć trybu nieskończone aby wskazać, że operacja jest wykonywana, ale że czas zakończenia jest nieznany.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych metod w `CMFCRibbonProgressBar` klasy. W przykładzie ustawiania pasek postępu do pracy w trybie nieskończone (gdzie czas ukończenia operacji jest nieznany), ustaw wartość minimalną i maksymalną dla paska postępu i ustaw bieżąca pozycja paska postępu. Następujący fragment kodu jest częścią [próbka MS Office 2007 Demo](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxRibbonProgressBar.h  
  
##  <a name="cmfcribbonprogressbar"></a>CMFCRibbonProgressBar::CMFCRibbonProgressBar  
 Tworzy i inicjuje [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md) obiektu.  
  
```  
CMFCRibbonProgressBar();

 
CMFCRibbonProgressBar(
    UINT nID,  
    int nWidth = 90,  
    int nHeight = 22);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nID`  
 Określa identyfikator polecenia pasek postępu wstążki.  
  
 [in]`nWidth`  
 Określa szerokość w pikselach, pasek postępu wstążki.  
  
 [in]`nHeight`  
 Określa wysokość w pikselach, pasek postępu wstążki.  
  
##  <a name="getpos"></a>CMFCRibbonProgressBar::GetPos  
 Zwraca bieżącą pozycję pasek postępu.  
  
```  
int GetPos () const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość reprezentującą bieżąca pozycja paska postępu.  
  
### <a name="remarks"></a>Uwagi  
 Zakres ustawiany musi znajdować się w zakresie określonym przez [CMFCRibbonProgressBar::SetRange](#setrange) metody.  
  
##  <a name="getrangemax"></a>CMFCRibbonProgressBar::GetRangeMax  
 Zwraca bieżącego użytkownika pasek postępu wartość maksymalna.  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna wartość bieżącego zakresu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getrangemin"></a>CMFCRibbonProgressBar::GetRangeMin  
 Zwraca bieżącego użytkownika pasek postępu minimalną wartość zakresu.  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Minimalna wartość bieżącego zakresu.  
  
##  <a name="getregularsize"></a>CMFCRibbonProgressBar::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isinfinitemode"></a>CMFCRibbonProgressBar::IsInfiniteMode  
 Określa, czy pasek postępu działa w trybie nieskończoną.  
  
```  
BOOL IsInfiniteMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli pasek postępu jest w trybie nieskończone; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 W trybie nieskończone pasek postępu wypełnia wielokrotnie z wartością minimalną wartość maksymalna. Można użyć trybu nieskończone aby wskazać, że operacja jest wykonywana, ale że czas zakończenia jest nieznany.  
  
##  <a name="ondraw"></a>CMFCRibbonProgressBar::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setinfinitemode"></a>CMFCRibbonProgressBar::SetInfiniteMode  
 Ustawia pasek postępu do pracy w trybie nieskończoną.  
  
```  
void SetInfiniteMode(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bSet`  
 `TRUE`Aby określić, czy pasek postępu jest w trybie nieskończone; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Zwykle Jeśli pasek postępu jest w trybie nieskończone, go informuje użytkownika czy operacja jest wykonywana, ale że czas zakończenia jest nieznany. W związku z tym pasek postępu wypełnia wielokrotnie z wartością minimalną wartość maksymalna.  
  
##  <a name="setpos"></a>CMFCRibbonProgressBar::SetPos  
 Ustawia bieżąca pozycja paska postępu.  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nPos`  
 Określa położenie, do którego jest ustawiona na pasku postępu.  
  
 [in]`bRedraw`  
 Określa, czy pasek postępu powinien być narysowany ponownie.  
  
### <a name="remarks"></a>Uwagi  
 Zakres ustawiany musi znajdować się w zakresie określonym przez [CMFCRibbonProgressBar::SetRange](#setrange) metody.  
  
##  <a name="setrange"></a>CMFCRibbonProgressBar::SetRange  
 Ustawia wartości minimalną i maksymalną dla pasek postępu.  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nMin`  
 Określa minimalną wartość zakresu.  
  
 [in]`nMax`  
 Określa maksymalną wartość zakresu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia zdefiniowanie zakresu pasek postępu przez ustawienie wartości minimalną i maksymalną.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
