---
title: Struktura ATL_DRAWINFO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
dev_langs:
- C++
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76f21f93bbd8386bbf0b4b63f3cf7c8b34057145
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210660"
---
# <a name="atldrawinfo-structure"></a>Struktura ATL_DRAWINFO
Zawiera informacje używane do renderowania do różnych celów, takich jak drukarki, metaplik lub kontrolki ActiveX.  
  
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
 Rozmiar struktury, w bajtach.  
  
 `dwDrawAspect`  
 Określa, jak element docelowy ma być reprezentowana. Oświadczenia mogą zawierać zawartość, ikony, miniaturę lub wydrukować dokument. Aby uzyskać listę możliwych wartości, zobacz [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect) i [DVASPECT2](/windows/desktop/api/ocidl/ne-ocidl-tagdvaspect2).  
  
 `lindex`  
 Część obiektu docelowego, który ma znaczenie dla operacji rysowania. Interpretację różni się zależnie od wartości w `dwDrawAspect` elementu członkowskiego.  
  
 `ptd`  
 Wskaźnik do [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) strukturę, która umożliwia rysowanie optymalizacje w zależności od aspekt określony. Należy pamiętać, że nowszej obiektów i kontenerów, które obsługuje zoptymalizowanego rysowania interfejsów obsługują także tego elementu członkowskiego. Starsze obiektów i kontenerów, które nie obsługują zoptymalizowanego rysowania interfejsów, zawsze należy określić wartość NULL dla tego elementu członkowskiego.  
  
 `hicTargetDev`  
 Informacje kontekstu dla urządzeń docelowych, wskazywana przez `ptd` z którego obiekt można wyodrębnić metryki urządzenia i przetestować jego możliwości. Jeśli `ptd` ma wartość NULL, obiekt powinien ignorować wartość `hicTargetDev` elementu członkowskiego.  
  
 `hdcDraw`  
 Kontekst urządzenia, na którym do rysowania. Dla obiektu bez okien `hdcDraw` element członkowski znajduje się w `MM_TEXT` tryb mapowania przy użyciu współrzędnych logiczne dopasowanie współrzędne klienta okna nadrzędnego. Ponadto, kontekst urządzenia powinna być w tym samym stanie, co zwykle przekazywane przez `WM_PAINT` wiadomości.  
  
 `prcBounds`  
 Wskaźnik do [RECTL](https://msdn.microsoft.com/library/windows/desktop/dd162907) struktury, określając prostokąta `hdcDraw` , w którym ma być rysowany obiektu. Ten element kontroluje pozycjonowanie i rozciąganie obiektu. Ten element członkowski powinna być równa NULL, aby narysować niepowiązanej z oknami aktywnego obiektu w miejscu. W każdej sytuacji o wartości NULL nie jest dozwoloną wartością i powinna być rozwiązywana we `E_INVALIDARG` kod błędu. Jeśli kontener przekazuje wartość inną niż NULL do obiektu bez okien, obiekt ma być renderowany żądany aspekt w kontekście określonego urządzenia i prostokąt. Kontener poprosić to obiekt bez okien do renderowania widoku w drugim, nieaktywnej obiektu lub drukowanie obiektu.  
  
 `prcWBounds`  
 Jeśli `hdcDraw` jest kontekście urządzenia metaplików (zobacz [GetDeviceCaps](/windows/desktop/api/wingdi/nf-wingdi-getdevicecaps) w zestawie Windows SDK), jest to wskaźnik do `RECTL` struktury, określając prostokąt otaczający w podstawowej metaplik. Struktura prostokąt zawiera rozmiaru okna i okna źródła. Wartości te są przydatne do rysowania metapliki. Prostokąt wskazywanym przez `prcBounds` zagnieździć to `prcWBounds` prostokąt; znajdują się w tej samej przestrzeni współrzędnych.  
  
 `bOptimize`  
 Różna od zera, jeśli rysunek formantu być optymalizowane, w przeciwnym razie 0. Jeśli rysunek jest optymalizowane, stan kontekstu urządzenia zostanie automatycznie przywrócony po zakończeniu renderowania.  
  
 `bZoomed`  
 Różna od zera, jeśli element docelowy ma współczynnika powiększenia, w przeciwnym razie 0. Współczynnika powiększenia jest przechowywany w `ZoomNum`.  
  
 `bRectInHimetric`  
 Jeśli wartość różną od zera wymiary `prcBounds` znajdują się w HIMETRIC, w przeciwnym razie 0.  
  
 `ZoomNum`  
 Szerokość i wysokość prostokąta, w którym obiekt jest renderowany. Współczynnika powiększenia wzdłuż osi x (część naturalnych rozmiar obiektu w jego bieżącym stopniu) obiektu docelowego jest wartością `ZoomNum.cx` podzieloną przez wartość `ZoomDen.cx`. W podobny sposób uzyskuje się współczynnika powiększenia wzdłuż osi y.  
  
 `ZoomDen`  
 Rzeczywiste szerokość i wysokość elementu docelowego.  
  
## <a name="remarks"></a>Uwagi  
 Typowy tej struktury jest pobieranie informacji podczas renderowania obiektu docelowego. Na przykład, można pobrać wartości z ATL_DRAWINFO wewnątrz swojej przeciążenia [CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).  
  
 Ta struktura przechowuje odpowiednie informacje używane do renderowania wygląd obiektu dla urządzenia. Informacje podane może służyć w rysunku do ekranu, drukarki lub nawet metaplik.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
## <a name="see-also"></a>Zobacz też  
  [Klasy i struktury](../../atl/reference/atl-classes.md) [IViewObject::Draw](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-draw)   
 [CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)





