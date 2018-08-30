---
title: Zmiana symbolu&#39;wartość liczbową s | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing.value
dev_langs:
- C++
helpviewer_keywords:
- numeric values
- symbols, numeric values
- numeric values, changing symbols
ms.assetid: 468e903b-9c07-4251-ae09-3b6cb754cc2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c05c732f87434754fb6776d7f914b4ffa5c26015
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219279"
---
# <a name="changing-a-symbol39s-numeric-value"></a>Zmiana symbolu&#39;wartość liczbową s

Symbole skojarzone z pojedynczego zasobu, można użyć [okno właściwości](/visualstudio/ide/reference/properties-window) Aby zmienić wartość symbol. Możesz użyć [okno dialogowe symboli zasobów](../windows/resource-symbols-dialog-box.md) zmianę wartości symboli nie jest aktualnie przypisany do zasobu. Aby uzyskać więcej informacji, zobacz [zmiana nieprzypisanych symboli](../windows/changing-unassigned-symbols.md).

### <a name="to-change-a-symbol-value-assigned-to-a-single-resource-or-object"></a>Aby zmienić wartość symbol przypisane do jednego zasobu lub obiektu

1. W [widok zasobów](../windows/resource-view-window.md), wybierz zasób.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. W **właściwości** okna, typ nazwy symbolu następuje znak równości i całkowitą **identyfikator** polu, na przykład:

    ```
    IDC_EDITNAME=5100
    ```

Nowa wartość są przechowywane w pliku nagłówkowym symboli podczas następnego zapisany projekt. Tylko nazwa symbolu pozostaje widoczna w polu Identyfikator; znak równości i wartości nie są wyświetlane po ich są prawidłowe.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Instrukcje dotyczące ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów wyświetlania statycznych zasobów i przydzielanie zasobów ciągów do właściwości.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Ograniczenia dotyczące wartości symbolu](../windows/symbol-value-restrictions.md)  
[Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)