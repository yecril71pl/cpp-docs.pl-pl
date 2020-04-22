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
ms.openlocfilehash: fb50f49d387e8620f3d5bbb41263738adbd8b437
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748805"
---
# <a name="atl_drawinfo-structure"></a>Struktura ATL_DRAWINFO

Zawiera informacje używane do renderowania do różnych obiektów docelowych, takich jak drukarka, metaplik lub formant ActiveX.

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
Rozmiar struktury w bajtach.

`dwDrawAspect`<br/>
Określa sposób reprezentowania obiektu docelowego. Reprezentacje mogą zawierać zawartość, ikonę, miniaturę lub wydrukowany dokument. Aby uzyskać listę możliwych wartości, zobacz [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) i [DVASPECT2](/windows/win32/api/ocidl/ne-ocidl-dvaspect2).

`lindex`<br/>
Część obiektu docelowego, która jest przedmiotem zainteresowania dla operacji rysowania. Jego interpretacja różni się w `dwDrawAspect` zależności od wartości w wemieć.

`ptd`<br/>
Wskaźnik do konstrukcji [DVTARGETDEVICE,](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) która umożliwia optymalizację rysowania w zależności od określonego aspektu. Należy zauważyć, że nowsze obiekty i kontenery, które obsługują zoptymalizowane interfejsy rysunku obsługują ten element członkowski. Starsze obiekty i kontenery, które nie obsługują zoptymalizowanych interfejsów rysunku, zawsze określają wartość NULL dla tego elementu członkowskiego.

`hicTargetDev`<br/>
Kontekst informacji dla urządzenia docelowego wskazywu, za pomocą `ptd` którego obiekt może wyodrębnić metryki urządzenia i przetestować możliwości urządzenia. Jeśli `ptd` jest null, obiekt powinien zignorować wartość w weszłnew. `hicTargetDev`

`hdcDraw`<br/>
Kontekst urządzenia, na którym można rysować. W przypadku obiektu bez `hdcDraw` okien element `MM_TEXT` członkowski znajduje się w trybie mapowania ze współrzędnymi logicznymi pasującymi do współrzędnych klienta okna zawierającego. Ponadto kontekst urządzenia powinien być w tym samym stanie, co `WM_PAINT` ten, który zwykle jest przekazywany przez wiadomość.

`prcBounds`<br/>
Wskaźnik do struktury [RECTL](/windows/win32/api/windef/ns-windef-rectl) określające prostokąt `hdcDraw` na i w którym obiekt powinien być rysowany. Ten element członkowski steruje pozycjonowaniem i rozciąganiem obiektu. Ten element członkowski powinien być NULL, aby narysować obiekt aktywny bez okien. W każdej innej sytuacji NULL nie jest wartością `E_INVALIDARG` prawną i powinien spowodować kod błędu. Jeśli kontener przekazuje wartość inną niż NULL do obiektu bez okien, obiekt powinien renderować żądany aspekt w określonym kontekście urządzenia i prostokącie. Kontener może zażądać tego z obiektu bez okien, aby renderować drugi, nieaktywny widok obiektu lub wydrukować obiekt.

`prcWBounds`<br/>
Jeśli `hdcDraw` jest kontekstem urządzenia metaplikowego (zobacz [GetDeviceCaps](/windows/win32/api/wingdi/nf-wingdi-getdevicecaps) w windows SDK), jest to wskaźnik do `RECTL` struktury określającej prostokąt ograniczający w podstawowym metapliku. Struktura prostokąta zawiera zakres okna i początek okna. Wartości te są przydatne do rysowania metaplików. Prostokąt wskazany przez `prcBounds` jest zagnieżdżony wewnątrz tego `prcWBounds` prostokąta; znajdują się w tej samej przestrzeni współrzędnych.

`bOptimize`<br/>
Nonzero, jeśli rysunek formantu ma być zoptymalizowany, w przeciwnym razie 0. Jeśli rysunek jest zoptymalizowany, stan kontekstu urządzenia jest automatycznie przywracany po zakończeniu renderowania.

`bZoomed`<br/>
Niezerowe, jeśli obiekt docelowy ma współczynnik powiększenia, w przeciwnym razie 0. Współczynnik powiększenia jest przechowywany w pliku `ZoomNum`.

`bRectInHimetric`<br/>
Nonzero, jeśli `prcBounds` wymiary są w HIMETRIC, w przeciwnym razie 0.

`ZoomNum`<br/>
Szerokość i wysokość prostokąta, do którego renderowany jest obiekt. Współczynnik powiększenia wzdłuż osi x (proporcja naturalnego rozmiaru obiektu do jego aktualnego `ZoomNum.cx` zasięgu) celu `ZoomDen.cx`jest wartością podzieloną przez wartość . Współczynnik powiększenia wzdłuż osi y jest osiągany w podobny sposób.

`ZoomDen`<br/>
Rzeczywista szerokość i wysokość obiektu docelowego.

## <a name="remarks"></a>Uwagi

Typowe użycie tej struktury byłoby pobieranie informacji podczas renderowania obiektu docelowego. Na przykład można pobrać wartości z ATL_DRAWINFO wewnątrz przeciążenia [CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).

Ta struktura przechowuje istotne informacje używane do renderowania wygląd obiektu dla urządzenia docelowego. Podane informacje mogą być używane do rysowania na ekranie, w drukarce, a nawet w metapliku.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="see-also"></a>Zobacz też

[Klasy i struktury](../../atl/reference/atl-classes.md)<br/>
[IViewObject::Draw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
