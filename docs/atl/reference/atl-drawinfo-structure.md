---
title: Struktura ATL_DRAWINFO
ms.date: 11/04/2016
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
ms.openlocfilehash: 70329d3b2c18c8cd8e94854f40ff971c0b39a8f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261068"
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

`cbSize`<br/>
Rozmiar struktury, w bajtach.

`dwDrawAspect`<br/>
Określa, jak element docelowy ma być reprezentowana. Oświadczenia mogą zawierać zawartość, ikony, miniaturę lub wydrukować dokument. Aby uzyskać listę możliwych wartości, zobacz [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect) i [DVASPECT2](/windows/desktop/api/ocidl/ne-ocidl-tagdvaspect2).

`lindex`<br/>
Część obiektu docelowego, który ma znaczenie dla operacji rysowania. Interpretację różni się zależnie od wartości w `dwDrawAspect` elementu członkowskiego.

`ptd`<br/>
Wskaźnik do [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) strukturę, która umożliwia rysowanie optymalizacje w zależności od aspekt określony. Należy pamiętać, że nowszej obiektów i kontenerów, które obsługuje zoptymalizowanego rysowania interfejsów obsługują także tego elementu członkowskiego. Starsze obiektów i kontenerów, które nie obsługują zoptymalizowanego rysowania interfejsów, zawsze należy określić wartość NULL dla tego elementu członkowskiego.

`hicTargetDev`<br/>
Informacje kontekstu dla urządzeń docelowych, wskazywana przez `ptd` z którego obiekt można wyodrębnić metryki urządzenia i przetestować jego możliwości. Jeśli `ptd` ma wartość NULL, obiekt powinien ignorować wartość `hicTargetDev` elementu członkowskiego.

`hdcDraw`<br/>
Kontekst urządzenia, na którym do rysowania. Dla obiektu bez okien `hdcDraw` element członkowski znajduje się w `MM_TEXT` tryb mapowania przy użyciu współrzędnych logiczne dopasowanie współrzędne klienta okna nadrzędnego. Ponadto, kontekst urządzenia powinna być w tym samym stanie, co zwykle przekazywane przez `WM_PAINT` wiadomości.

`prcBounds`<br/>
Wskaźnik do [RECTL](https://msdn.microsoft.com/library/windows/desktop/dd162907) struktury, określając prostokąta `hdcDraw` , w którym ma być rysowany obiektu. Ten element kontroluje pozycjonowanie i rozciąganie obiektu. Ten element członkowski powinna być równa NULL, aby narysować niepowiązanej z oknami aktywnego obiektu w miejscu. W każdej sytuacji o wartości NULL nie jest dozwoloną wartością i powinna być rozwiązywana we `E_INVALIDARG` kod błędu. Jeśli kontener przekazuje wartość inną niż NULL do obiektu bez okien, obiekt ma być renderowany żądany aspekt w kontekście określonego urządzenia i prostokąt. Kontener poprosić to obiekt bez okien do renderowania widoku w drugim, nieaktywnej obiektu lub drukowanie obiektu.

`prcWBounds`<br/>
Jeśli `hdcDraw` jest kontekście urządzenia metaplików (zobacz [GetDeviceCaps](/windows/desktop/api/wingdi/nf-wingdi-getdevicecaps) w zestawie Windows SDK), jest to wskaźnik do `RECTL` struktury, określając prostokąt otaczający w podstawowej metaplik. Struktura prostokąt zawiera rozmiaru okna i okna źródła. Wartości te są przydatne do rysowania metapliki. Prostokąt wskazywanym przez `prcBounds` zagnieździć to `prcWBounds` prostokąt; znajdują się w tej samej przestrzeni współrzędnych.

`bOptimize`<br/>
Różna od zera, jeśli rysunek formantu być optymalizowane, w przeciwnym razie 0. Jeśli rysunek jest optymalizowane, stan kontekstu urządzenia zostanie automatycznie przywrócony po zakończeniu renderowania.

`bZoomed`<br/>
Różna od zera, jeśli element docelowy ma współczynnika powiększenia, w przeciwnym razie 0. Współczynnika powiększenia jest przechowywany w `ZoomNum`.

`bRectInHimetric`<br/>
Jeśli wartość różną od zera wymiary `prcBounds` znajdują się w HIMETRIC, w przeciwnym razie 0.

`ZoomNum`<br/>
Szerokość i wysokość prostokąta, w którym obiekt jest renderowany. Współczynnika powiększenia wzdłuż osi x (część naturalnych rozmiar obiektu w jego bieżącym stopniu) obiektu docelowego jest wartością `ZoomNum.cx` podzieloną przez wartość `ZoomDen.cx`. W podobny sposób uzyskuje się współczynnika powiększenia wzdłuż osi y.

`ZoomDen`<br/>
Rzeczywiste szerokość i wysokość elementu docelowego.

## <a name="remarks"></a>Uwagi

Typowy tej struktury jest pobieranie informacji podczas renderowania obiektu docelowego. Na przykład, można pobrać wartości z ATL_DRAWINFO wewnątrz swojej przeciążenia [CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).

Ta struktura przechowuje odpowiednie informacje używane do renderowania wygląd obiektu dla urządzenia. Informacje podane może służyć w rysunku do ekranu, drukarki lub nawet metaplik.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../../atl/reference/atl-classes.md)<br/>
[IViewObject::Draw](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
