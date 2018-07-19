---
title: Klasa CMFCRibbonProgressBar | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eec19c574d9555fdfefaedd1b5ac05d896d15152
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850764"
---
# <a name="cmfcribbonprogressbar-class"></a>Klasa CMFCRibbonProgressBar
Implementuje formant, który wizualnie wskazuje postęp długiej operacji.  
  
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
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|Określa, czy pasek postępu działa w trybie nieskończone.|  
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|Metoda wywoływana przez platformę, by narysować elementem wstążki. (Przesłania [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|  
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|Ustawia pasek postępu do pracy w trybie nieskończone.|  
|[CMFCRibbonProgressBar::SetPos](#setpos)|Ustawia bieżący postęp.|  
|[CMFCRibbonProgressBar::SetRange](#setrange)|Ustawia wartości minimalne i maksymalne.|  
  
## <a name="remarks"></a>Uwagi  
 Element `CMFCRibbonProgressBar` może działać w dwóch trybach: regularne i nieskończona. W regularnym trybie paska postępu jest wypełniany od lewej do prawej i zatrzymuje się wartość maksymalna. W trybie nieskończoną pasek postępu jest wielokrotnie wypełnione z minimalną wartość maksymalnej wartości. Można użyć trybu nieskończonej aby wskazać, że trwa operacja, ale że czas ukończenia jest nieznany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak korzystać z różnych metod w `CMFCRibbonProgressBar` klasy. W przykładzie pokazano sposób ustawiania pasek postępu do pracy w trybie infinite (których czas ukończenia operacji jest nieznany), ustawienie minimalne i maksymalne wartości dla paska postępu i ustawienie bieżącej pozycji pasek postępu. Ten fragment kodu jest częścią [próbka MS Office 2007 Demo](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxRibbonProgressBar.h  
  
##  <a name="cmfcribbonprogressbar"></a>  CMFCRibbonProgressBar::CMFCRibbonProgressBar  
 Tworzy i inicjuje [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md) obiektu.  
  
```  
CMFCRibbonProgressBar();

 
CMFCRibbonProgressBar(
    UINT nID,  
    int nWidth = 90,  
    int nHeight = 22);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nID*  
 Określa identyfikator polecenia dla paska postępu wstążki.  
  
 [in] *nWidth*  
 Określa szerokość w pikselach, na wstążce paska postępu.  
  
 [in] *nHeight*  
 Określa wysokość w pikselach, na wstążce paska postępu.  
  
##  <a name="getpos"></a>  CMFCRibbonProgressBar::GetPos  
 Zwraca bieżącą pozycję pasek postępu.  
  
```  
int GetPos () const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość reprezentująca bieżącego położenia obiektu pasek postępu.  
  
### <a name="remarks"></a>Uwagi  
 Zakres ustawiania musi być w zakresie określonym przez [CMFCRibbonProgressBar::SetRange](#setrange) metody.  
  
##  <a name="getrangemax"></a>  CMFCRibbonProgressBar::GetRangeMax  
 Zwraca pasek postępu jego bieżąca wartość maksymalna.  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna wartość bieżącego zakresu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getrangemin"></a>  CMFCRibbonProgressBar::GetRangeMin  
 Zwraca bieżącego użytkownika na pasku postępu minimalną wartość zakresu.  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość minimalna bieżącego zakresu.  
  
##  <a name="getregularsize"></a>  CMFCRibbonProgressBar::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isinfinitemode"></a>  CMFCRibbonProgressBar::IsInfiniteMode  
 Określa, czy pasek postępu działa w trybie nieskończone.  
  
```  
BOOL IsInfiniteMode() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli pasek postępu jest w trybie nieskończona w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 W trybie nieskończonej pasek postępu wypełni wielokrotnie z minimalną wartość maksymalnej wartości. Można użyć trybu nieskończonej aby wskazać, że trwa operacja, ale że czas ukończenia jest nieznany.  
  
##  <a name="ondraw"></a>  CMFCRibbonProgressBar::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setinfinitemode"></a>  CMFCRibbonProgressBar::SetInfiniteMode  
 Ustawia pasek postępu do pracy w trybie nieskończone.  
  
```  
void SetInfiniteMode(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bUstawienie*  
 Wartość TRUE, aby określić, że pasek postępu jest w trybie nieskończonej; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Zwykle Jeśli pasek postępu jest w trybie nieskończoną, jego informacją dla użytkownika, trwa operacja, ale że czas ukończenia jest nieznany. W związku z tym pasek postępu wypełni wielokrotnie z minimalną wartość maksymalnej wartości.  
  
##  <a name="setpos"></a>  CMFCRibbonProgressBar::SetPos  
 Ustawia bieżącej pozycji pasek postępu.  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *npos —*  
 Określa położenie, do którego ustawiono pasek postępu.  
  
 [in] *bRedraw*  
 Określa, czy pasek postępu powinien być narysowany ponownie.  
  
### <a name="remarks"></a>Uwagi  
 Zakres ustawiania musi być w zakresie określonym przez [CMFCRibbonProgressBar::SetRange](#setrange) metody.  
  
##  <a name="setrange"></a>  CMFCRibbonProgressBar::SetRange  
 Określa minimalne i maksymalne wartości dla paska postępu.  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *Nmin.*  
 Określa wartość minimum zakresu.  
  
 [in] *nmaks.*  
 Określa maksymalną wartość zakresu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia zdefiniowanie zakresu pasek postępu, ustawiając wartości minimalne i maksymalne.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
