---
title: Typy list obrazów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lists [MFC], image
- image lists [MFC], types of
- CImageList class [MFC], types
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bea24d487170ea4cac470f2244340f6b570d1ec
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390477"
---
# <a name="types-of-image-lists"></a>Typy list obrazów

Istnieją dwa typy list obrazów ([CImageList](../mfc/reference/cimagelist-class.md)): nonmasked i maskowanego. "Lista nonmasked obrazu" składa się z mapy bitowej kolor, który zawiera jeden lub więcej obrazów. "Lista maskowanego obrazu" składa się z dwóch map bitowych w taki sam rozmiar. Pierwsza to kolorów mapy bitowej, który zawiera obrazy, a drugą jest wartość monochromatyczną mapę bitową, która zawiera szereg maski — jeden dla każdego obrazu w pierwszym mapy bitowej.

Jednego z przeciążeń `Create` funkcja elementu członkowskiego pobiera flagę wskazującą, czy lista obrazów są wyświetlane jako znaki. (Inne przeciążenia tworzenie list obrazów maskowanego).

Podczas rysowania obrazu nonmasked po prostu jest kopiowana do kontekstu urządzenia docelowego; oznacza to, że jej rysowania za pośrednictwem istniejących kolor tła kontekstu urządzenia. Podczas rysowania obrazu maskowanego bitów obrazu, są połączone z bity maski zazwyczaj tworzenie obszarów przezroczystych w mapie bitowej gdzie zawiera kolor tła kontekstu urządzenia docelowego za pomocą. Można określić kilka stylów rysunku, podczas rysowania obrazu maskowanego. Na przykład można określić, czy obraz być symulowane w celu wskazania wybranego obiektu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CImageList](../mfc/using-cimagelist.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

