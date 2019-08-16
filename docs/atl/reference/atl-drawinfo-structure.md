---
title: ATL_DRAWINFO, struktura
ms.date: 11/04/2016
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
ms.openlocfilehash: 728a7eed418a6600c9247b91ff7b777dd458e621
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498007"
---
# <a name="atl_drawinfo-structure"></a>ATL_DRAWINFO, struktura

Zawiera informacje służące do renderowania do różnych elementów docelowych, takich jak drukarka, metaplik lub Kontrolka ActiveX.

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
Określa sposób reprezentowania celu. Reprezentacje mogą zawierać zawartość, ikonę, miniaturę lub dokument drukowany. Aby uzyskać listę możliwych wartości, zobacz [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) i [DVASPECT2](/windows/win32/api/ocidl/ne-ocidl-dvaspect2).

`lindex`<br/>
Część elementu docelowego, który jest interesujący dla operacji rysowania. Interpretacja różni się w zależności od wartości `dwDrawAspect` elementu członkowskiego.

`ptd`<br/>
Wskaźnik na strukturę [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) , która umożliwia rysowanie optymalizacji w zależności od określonego aspektu. Należy pamiętać, że nowsze obiekty i kontenery obsługujące zoptymalizowane interfejsy rysowania obsługują również ten element członkowski. Starsze obiekty i kontenery, które nie obsługują zoptymalizowanych interfejsów rysowania, zawsze określają wartość NULL dla tego elementu członkowskiego.

`hicTargetDev`<br/>
Kontekst informacji dla urządzenia docelowego wskazywanego przez `ptd` , z którego obiekt może wyodrębnić metryki urządzeń i przetestować możliwości urządzenia. Jeśli `ptd` ma wartość null, obiekt powinien zignorować wartość `hicTargetDev` elementu członkowskiego.

`hdcDraw`<br/>
Kontekst urządzenia, na którym należy narysować. W przypadku obiektu `hdcDraw` bez okna element członkowski znajduje się `MM_TEXT` w trybie mapowania ze współrzędnymi logicznymi odpowiadającymi współrzędnymi klienta okna zawierającego. Ponadto kontekst urządzenia powinien znajdować się w tym samym stanie co ten, który zwykle jest przesyłany `WM_PAINT` przez komunikat.

`prcBounds`<br/>
Wskaźnik do struktury [Rect](/previous-versions//dd162907\(v=vs.85\)) , który określa prostokąt na `hdcDraw` i, w którym obiekt powinien być rysowany. Ten element członkowski kontroluje pozycjonowanie i rozciąganie obiektu. Ten element członkowski powinien mieć wartość NULL, aby narysować bezokienkowy obiekt aktywny. W każdej innej sytuacji wartość null nie jest wartością dozwoloną i powinna powodować `E_INVALIDARG` kod błędu. Jeśli kontener przekaże wartość różną od NULL do obiektu bez okna, obiekt powinien renderować żądany aspekt do określonego kontekstu i prostokąta urządzenia. Kontener może zażądać tego z obiektu bez okna, aby renderować drugi, nieaktywny widok obiektu lub wydrukować obiekt.

`prcWBounds`<br/>
Jeśli `hdcDraw` jest kontekstem urządzenia metapliku (zobacz [GetDeviceCaps](/windows/win32/api/wingdi/nf-wingdi-getdevicecaps) w Windows SDK), jest to wskaźnik do `RECTL` struktury określającej prostokąt ograniczający w źródłowym metapliku. Struktura prostokąta zawiera zakres okna i pochodzenie okna. Te wartości są przydatne do rysowania plików. Prostokąt wskazywany przez `prcBounds` jest zagnieżdżony wewnątrz `prcWBounds` tego prostokąta; znajdują się w tej samej przestrzeni współrzędnych.

`bOptimize`<br/>
Różne od zera, Jeśli rysunek kontrolki ma być zoptymalizowany, w przeciwnym razie 0. Jeśli rysunek jest zoptymalizowany, stan kontekstu urządzenia jest automatycznie przywracany po zakończeniu renderowania.

`bZoomed`<br/>
Różne od zera, jeśli element docelowy ma współczynnik powiększenia, w przeciwnym razie 0. Współczynnik powiększenia jest przechowywany w `ZoomNum`.

`bRectInHimetric`<br/>
Różne od zera, jeśli wymiary `prcBounds` są w HIMETRIC, w przeciwnym razie 0.

`ZoomNum`<br/>
Szerokość i wysokość prostokąta, do którego jest renderowany obiekt. Współczynnik powiększenia wzdłuż osi x (proporcja rozmiaru naturalnego obiektu do jego bieżącego zakresu) obiektu docelowego jest wartością `ZoomNum.cx` podzieloną przez `ZoomDen.cx`wartość. Współczynnik powiększenia wzdłuż osi y jest osiągany w podobny sposób.

`ZoomDen`<br/>
Rzeczywista szerokość i wysokość celu.

## <a name="remarks"></a>Uwagi

Typowym użyciem tej struktury będzie pobieranie informacji podczas renderowania obiektu docelowego. Na przykład można pobrać wartości z ATL_DRAWINFO wewnątrz przeciążenia [CComControlBase:: OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).

Ta struktura przechowuje odpowiednie informacje używane do renderowania wyglądu obiektu dla urządzenia docelowego. Podane informacje mogą służyć do rysowania na ekranie, drukarce, a nawet w metaplikach.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../../atl/reference/atl-classes.md)<br/>
[Widok IViewobject::D RAW](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
