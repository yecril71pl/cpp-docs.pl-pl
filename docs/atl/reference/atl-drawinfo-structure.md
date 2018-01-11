---
title: Struktura ATL_DRAWINFO | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
dev_langs: C++
helpviewer_keywords: ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 70ea9b2532b8ab63bc9c840e7e08790b3af57342
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="atldrawinfo-structure"></a>Struktura ATL_DRAWINFO
Zawiera informacje używane do renderowania do różnych celów, takich jak drukarki, metaplik lub formantu ActiveX.  
  
## <a name="syntax"></a>Składnia  
  
```
struct ATL_DRAWINFO {
    UINT cbSize;
    DWORD dwDrawAspect;
    LONG lindex;
    DVTARGETDEVICE* ptd;
    HDC hicTargetDev;
    HDC hdcDraw;
    LPCRECTL prcBounds;
    LPCRECTL prcWBounds;
    BOOL bOptimize;
    BOOL bZoomed;
    BOOL bRectInHimetric;
    SIZEL ZoomNum;
    SIZEL ZoomDen;
};
```  
  
## <a name="members"></a>Elementy członkowskie  
 `cbSize`  
 Rozmiar w bajtach struktury.  
  
 **dwDrawAspect**  
 Określa, jak element docelowy ma być reprezentowane. Oświadczenia mogą zawierać zawartość, ikona, miniaturę lub wydrukować dokument. Aby uzyskać listę możliwych wartości, zobacz [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) i [DVASPECT2](http://msdn.microsoft.com/library/windows/desktop/ms688644).  
  
 **wartość lindex.**  
 Część docelowego, który ma znaczenie dla operacji rysowania. Interpretacji może być różna w zależności od wartości w **dwDrawAspect** elementu członkowskiego.  
  
 **PTD**  
 Wskaźnik do [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) strukturę, która włącza optymalizacje rysowania w zależności od aspekt określony. Należy zauważyć, że nowszej obiektów i kontenerów, które obsługuje zoptymalizowanego rysowania interfejsów obsługuje również tego elementu członkowskiego. Określ starszych obiektów i kontenerów, które nie obsługują zoptymalizowanego rysowania interfejsy zawsze **NULL** dla tego elementu członkowskiego.  
  
 **hicTargetDev**  
 Informacje o kontekście dla urządzenia wskazywana przez **ptd** z której obiekt można wyodrębnić metryki urządzenia i testowanie możliwości urządzenia. Jeśli **ptd** jest **NULL**, obiekt ignorować wartość **hicTargetDev** elementu członkowskiego.  
  
 **hdcDraw**  
 Kontekst urządzenia, na którym ma zostać narysowany. Dla obiekt bez okien **hdcDraw** członek `MM_TEXT` tryb mapowania z współrzędnych logiczną odpowiadającym współrzędne klienta okna nadrzędnego. Ponadto kontekstu urządzenia powinien być w tym samym stanie, co zwykle przekazany przez `WM_PAINT` wiadomości.  
  
 **prcBounds**  
 Wskaźnik do [RECTL](http://msdn.microsoft.com/library/windows/desktop/dd162907) struktury Określanie prostokąt na **hdcDraw** , w którym ma być rysowany obiektu. Ten element członkowski steruje pozycjonowanie i rozciąganie obiektu. Ten element członkowski powinien być **NULL** do rysowania bez okien w miejscu aktywnego obiektu. W każdej sytuacji **NULL** nie jest dozwoloną wartością i powinno spowodować `E_INVALIDARG` kod błędu. Jeśli kontener przekazuje niż**NULL** wartość do obiektu bez okien, obiekt powinien renderować żądany aspekt w kontekście określonego urządzenia i prostokąta. Kontener może poprosić to bez okien obiektu do renderowania widoku drugiej, nieaktywnych obiektu lub do drukowania obiektu.  
  
 **prcWBounds**  
 Jeśli **hdcDraw** jest kontekst urządzenia metafile (zobacz [GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877) w zestawie Windows SDK), jest wskaźnik do **RECTL** Określanie prostokąt ograniczający w strukturze podstawowy metaplik. Struktura prostokąt zawiera zakres okna i pochodzenia okna. Wartości te są przydatne w przypadku rysowania metapliki. Prostokąt wskazywanym przez **prcBounds** zagnieżdżona to **prcWBounds** prostokąt; znajdują się w tej samej przestrzeni współrzędnych.  
  
 **bOptimize**  
 Różna od zera, jeśli rysunek formantu ma być zoptymalizowany, w przeciwnym razie 0. Jeśli rysunku jest optymalizowane, stan kontekstu urządzenia zostanie automatycznie przywrócony po zakończeniu renderowania.  
  
 **bZoomed**  
 Różna od zera, jeśli element docelowy ma współczynnika powiększenia, w przeciwnym razie wartość 0. Współczynnika powiększenia jest przechowywany w **ZoomNum**.  
  
 **bRectInHimetric**  
 Jeśli podano niezerowe wymiary **prcBounds** w **HIMETRIC**, w przeciwnym razie wartość 0.  
  
 **ZoomNum**  
 Szerokość i wysokość prostokąta, do którego jest renderowany obiektu. Współczynnika powiększenia wzdłuż osi x (część fizycznych rozmiar obiektu w jego bieżącym zakresie) obiektu docelowego jest wartością **ZoomNum.cx** podzielona przez wartość **ZoomDen.cx**. W podobny sposób uzyskuje się współczynnika powiększenia wzdłuż osi y.  
  
 **ZoomDen**  
 Rzeczywista szerokość i wysokość elementu docelowego.  
  
## <a name="remarks"></a>Uwagi  
 Typowy sposób ta struktura jest pobieranie informacji podczas renderowania obiektu docelowego. Na przykład można pobrać wartości z `ATL_DRAWINFO` wewnątrz sieci przeciążenia [CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).  
  
 Ta struktura przechowuje odpowiednie informacje używane do renderowania wygląd obiektu dla urządzenia. Z informacji podanych może służyć rysunku ekranu, drukarki lub nawet metaplik.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury](../../atl/reference/atl-structures.md)   
 [IViewObject::Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)   
 [CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)





