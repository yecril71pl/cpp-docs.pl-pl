---
title: 'Symbole: Identyfikatory zasobów (C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.identifiers
dev_langs:
- C++
helpviewer_keywords:
- symbols [C++], resource identifiers
- symbols [C++], creating
- resource symbols
- symbols [C++], editing
- resource editors [C++], resource symbols
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c3bbcc774115311cd4ed0f302e4d9812ecfc6505
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422270"
---
# <a name="symbols-resource-identifiers-c"></a>Symbole: Identyfikatory zasobów (C++)

Symbol jest identyfikatorem zasobu (identyfikator), który składa się z dwóch części: ciąg tekstowy (nazwa symbolu) zamapowany na wartość całkowitą (wartość symbolu). Na przykład:

```
IDC_EDITNAME = 5100
```

Nazwy symboli w większości przypadków są określane jako identyfikatorów.

Symbole Podaj opisową sposób odwoływania się do zasobów i obiektów interfejsu użytkownika, zarówno w kodzie źródłowym, jak i podczas pracy z nimi w edytorach zasobów. Możesz wyświetlać i manipulować symboli w jednym wygodnym miejscu przy użyciu [okno dialogowe symboli zasobów](../windows/viewing-resource-symbols.md).

Podczas tworzenia nowego zasobu lub obiektu zasobu [edytory zasobów](../windows/resource-editors.md) Podaj nazwę domyślną dla danego zasobu, na przykład `IDC_RADIO1`i przypisać jej wartości. Definicja name plus wartość jest przechowywana w pliku Resource.h.

> [!NOTE]
> Podczas kopiowania zasobów lub obiektów zasobów z jednego pliku .rc do innego, Visual C++ mogą ulec zmianie, przeniesione zasób wartości symbolu lub nazwy symbolu i wartości, aby uniknąć konfliktów z nazwami symboli lub wartości z istniejącego pliku.

W miarę wzrostu aplikacji w rosnąca liczba i rozmiar, co powoduje jego ilość zasobów oraz symbole. Śledzenie dużą liczbę symboli, rozproszone w wielu plików może być trudne. [Okno dialogowe symboli zasobów](../windows/resource-symbols-dialog-box.md) upraszcza zarządzanie symboli, oferując narzędzie centralnego za pomocą którego można:

- [Wyświetlanie symboli zasobów](../windows/viewing-resource-symbols.md)

- [Tworzenie nowych symboli](../windows/creating-new-symbols.md)

- [Zmiana nieprzypisanych symboli](../windows/changing-unassigned-symbols.md)

- [Usuwanie nieprzypisanych symboli](../windows/deleting-unassigned-symbols.md)

- [Otwieranie Edytora zasobów dla podanego symbolu](../windows/opening-the-resource-editor-for-a-given-symbol.md)

- [Zmiana symbolu lub nazwy symbolu (ID)](../windows/changing-a-symbol-or-symbol-name-id.md)

- [Zmiana wartości numerycznej symbolu](../windows/changing-a-symbol-s-numeric-value.md)

- [Zmiana nazw symboli plików nagłówkowych](../windows/changing-the-names-of-symbol-header-files.md)

- [Obejmują udostępnionych (tylko do odczytu) lub obliczonych symboli](../windows/including-shared-read-only-or-calculated-symbols.md)

- [Wyświetl wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Instrukcje: wyszukiwanie symboli w zasobach](../windows/how-to-search-for-symbols-in-resources.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)