---
title: Identyfikatory zasobów (symbolom) (C++)
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
ms.openlocfilehash: c76b870ad1fdfeda7370af03c6396bedba9530ab
ms.sourcegitcommit: f127b08f114b8d6cab6b684febcb6f2ae0e055ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954864"
---
# <a name="resource-identifiers-symbols-c"></a>Identyfikatory zasobów (symbolom) (C++)

Symbol jest identyfikatorem zasobu (identyfikator), który składa się z dwóch części: ciąg tekstowy (nazwa symbolu) zamapowany na wartość całkowitą (wartość symbolu). Na przykład:

```
IDC_EDITNAME = 5100
```

Nazwy symboli w większości przypadków są określane jako identyfikatorów.

Symbole Podaj opisową sposób odwoływania się do zasobów i obiektów interfejsu użytkownika, zarówno w kodzie źródłowym, jak i podczas pracy z nimi w edytorach zasobów. Możesz wyświetlać i manipulować symboli w jednym wygodnym miejscu przy użyciu [okno dialogowe symboli zasobów](../windows/viewing-resource-symbols.md).

Podczas tworzenia nowego zasobu lub obiektu zasobu [edytory zasobów](../windows/resource-editors.md) Podaj nazwę domyślną dla danego zasobu, na przykład `IDC_RADIO1`i przypisać jej wartości. Definicja name plus wartość jest przechowywana w `Resource.h` pliku.

> [!NOTE]
> Podczas kopiowania zasobów lub obiektów zasobów z jednego pliku .rc do innego, Visual C++ mogą ulec zmianie, przeniesione zasób wartości symbolu lub nazwy symbolu i wartości, aby uniknąć konfliktów z nazwami symboli lub wartości z istniejącego pliku.

W miarę wzrostu aplikacji w rosnąca liczba i rozmiar, co powoduje jego ilość zasobów oraz symbole. Śledzenie dużą liczbę symboli, rozproszone w wielu plików może być trudne. **Symboli zasobów** okno dialogowe upraszcza zarządzanie symboli, oferując narzędzie centralnego za pomocą którego można:

- [Tworzenie symboli](../windows/creating-new-symbols.md)

- [Zarządzanie symboli](../windows/changing-a-symbol-or-symbol-name-id.md)

- [Wyświetl wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)<br/>