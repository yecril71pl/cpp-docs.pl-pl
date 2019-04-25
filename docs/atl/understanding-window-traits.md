---
title: Cech okna ATL
ms.date: 11/04/2016
helpviewer_keywords:
- window traits
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
ms.openlocfilehash: 29549e54051405fc3dd4d5d7ae70a382ad7a62ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196186"
---
# <a name="understanding-window-traits"></a>Opis cech okna

Okno cech klasy zapewniają w prosty sposób standaryzacji stylów używany do tworzenia obiektu ATL okna. Cech okna są akceptowane jako parametry szablonu przez [CWindowImpl](../atl/reference/cwindowimpl-class.md) i innych klas okien ATL jako sposób zapewnienia domyślne style okna ramowego na poziomie klasy.

Jeśli twórca wystąpienia okna nie udostępnia style jawnie w wywołaniu [Utwórz](../atl/reference/cwindowimpl-class.md#create), klasa cech umożliwia Sprawdź, czy okno jest nadal utworzone przy użyciu stylów poprawne. Nawet można zapewnić, że określone style są ustawione dla wszystkich wystąpień tej klasy okna umożliwiając innymi stylami, należy ustawić na podstawie poszczególnych wystąpień.

## <a name="atl-window-traits-templates"></a>Szablony cech okien ATL

ATL zawiera dwa szablony cech okna, które umożliwiają ustawianie domyślnych stylów w czasie kompilacji przy użyciu swoich parametrów szablonu.

|Class|Opis|
|-----------|-----------------|
|[CWinTraits](../atl/reference/cwintraits-class.md)|Użyj tego szablonu, które chcesz udostępnić domyślne style okna, które będą używane tylko wtedy, gdy nie inne style są określone w wywołaniu `Create`. Style podane w czasie wykonywania, mają pierwszeństwo przed za pośrednictwem style na czas kompilacji.|
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|Klasa jest używana, jeśli chcesz określić style, które musi zawsze być ustawiona dla klasy okna. Style dostarczane w czasie wykonywania są połączone ze stylami ustawiony w czasie kompilacji przy użyciu bitowego operatora OR.|

Oprócz tych szablonów ATL zawiera szereg wstępnie zdefiniowanych specjalizacje `CWinTraits` szablonu dla często używanych kombinacji Style okna ramowego. Zobacz [CWinTraits](../atl/reference/cwintraits-class.md) dokumentacji, aby uzyskać szczegółowe informacje.

## <a name="custom-window-traits"></a>Niestandardowe okno cech

W sytuacji, prawdopodobnie nie ten. wyspecjalizowanym szablonów, dostarczone przez ATL nie jest wystarczające i musisz utworzyć własne klasy cech, wystarczy utworzyć klasę, która implementuje dwie funkcje statyczne: `GetWndStyle` i `GetWndStyleEx`:

[!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/cpp/understanding-window-traits_1.h)]

Każda z tych funkcji zostanie przekazany jakąś wartość stylu w czasie wykonywania, którego można użyć do utworzenia nowej wartości stylu. Klasa cech okna, jest on używany jako argument szablonu do klasy okien ATL, styl przekazywana do tych funkcji statycznych spowoduje wartości niezależnie od rodzaju został przekazany jako argumenty styl [Utwórz](../atl/reference/cwindowimpl-class.md#create).

## <a name="see-also"></a>Zobacz także

[Klasy okien](../atl/atl-window-classes.md)
