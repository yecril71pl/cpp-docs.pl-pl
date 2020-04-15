---
title: Identyfikatory zasobów (symbole) (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.identifiers
helpviewer_keywords:
- symbols [C++], resource identifiers
- symbols [C++], creating
- resource symbols
- symbols [C++], editing
- resource editors [C++], resource symbols
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
ms.openlocfilehash: c6b3cf7d3edfc870164645632bb07bf49c792a48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359886"
---
# <a name="resource-identifiers-symbols-c"></a>Identyfikatory zasobów (symbole) (C++)

Symbol jest identyfikatorem zasobu (ID), który składa się z dwóch części, nazwy symbolu (ciągu tekstowego) mapowanych na wartość symbolu (liczba całkowita), na przykład:

```cpp
IDC_EDITNAME = 5100
```

Nazwy symboli są najczęściej określane jako identyfikatory.

Symbole zapewniają opisowy sposób odwoływania się do zasobów i obiektów interfejsu użytkownika, zarówno w kodzie źródłowym, jak i podczas pracy z nimi w edytorach zasobów. Symbole można wyświetlać i manipulować nimi w jednym wygodnym miejscu za pomocą [okna dialogowego Symbole zasobów](../windows/viewing-resource-symbols.md).

W miarę jak aplikacja rośnie w rozmiarze i wyrafinowaniu, podobnie jak jej liczba zasobów i symboli. Śledzenie dużej liczby symboli rozrzuconych po kilku plikach może być trudne. Okno **dialogowe Symbole zasobów** upraszcza zarządzanie symbolami, oferując centralne narzędzie, za pomocą którego można:

- [Tworzenie symboli](../windows/creating-new-symbols.md)

- [Zarządzanie symbolami](../windows/changing-a-symbol-or-symbol-name-id.md)

- [Wyświetlanie wstępnie zdefiniowanych identyfikatorów symboli](../windows/predefined-symbol-ids.md)

Podczas tworzenia nowego zasobu lub obiektu zasobów [edytory zasobów](../windows/resource-editors.md) podają domyślną nazwę zasobu, na przykład, `IDC_RADIO1`i przypisują do niego wartość. Definicja nazwa plus wartość jest `Resource.h` przechowywana w pliku.

> [!NOTE]
> Podczas kopiowania zasobów lub obiektów zasobów z jednego pliku rc do innego program Visual C++ może zmienić wartość symbolu przeniesionego zasobu lub nazwę i wartość symbolu, aby uniknąć konfliktów z nazwami symboli lub wartościami w istniejącym pliku.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)<br/>
