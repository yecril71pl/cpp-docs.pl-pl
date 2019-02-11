---
title: Zmienianie lub usuwanie nieprzypisanych symboli
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing.unassigned
helpviewer_keywords:
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
ms.assetid: b6abee4a-3c24-4697-a166-fe6a86cad35f
ms.openlocfilehash: 47cc3d7a387092afe77fdbcf4bbdb6d085eeda25
ms.sourcegitcommit: 966e4466f10c93fc12faf33d28e03b39489423fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987017"
---
# <a name="changing-or-deleting-unassigned-symbols"></a>Zmienianie lub usuwanie nieprzypisanych symboli

W [okno dialogowe symboli zasobów](../windows/resource-symbols-dialog-box.md), edytować lub usunąć istniejące symboli, które nie są już przypisane do zasobu lub obiektu.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*.

## <a name="to-change-an-unassigned-symbol"></a>Aby zmienić nieprzypisanych symboli

1. W **nazwa** wybierz nieprzypisanych symboli, a wybierz **zmiany**.

1. Edytuj nazwę symbolu lub wartości w polach w **Zmień Symbol** okno dialogowe.

   > [!NOTE]
   > Aby zmienić symbol, *jest* przypisany do zasobu lub obiektu, należy użyć edytora zasobów lub **właściwości** okna. Aby uzyskać więcej informacji, zobacz [zmiana symbolu lub nazwy symbolu](../windows/changing-a-symbol-or-symbol-name-id.md).

## <a name="to-delete-an-unassigned-unused-symbol"></a>Aby usunąć nieprzypisanych symboli (nieużywane)

W [okno dialogowe symboli zasobów](../windows/resource-symbols-dialog-box.md), wybierz symbol, który chcesz usunąć, a następnie wybierz **Usuń**.

   > [!NOTE]
   > Przed usunięciem nieużywane symboli w pliku zasobów, upewnij się, że nie jest on używany gdzie indziej w programie lub plików zasobów znajdujących się w czasie kompilacji.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Wyświetlanie symboli zasobów](../windows/viewing-resource-symbols.md)<br/>
[Ograniczenia dotyczące nazwy symbolu](../windows/symbol-name-restrictions.md)<br/>
[Ograniczenia dotyczące wartości symbolu](../windows/symbol-value-restrictions.md)<br/>
[Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)