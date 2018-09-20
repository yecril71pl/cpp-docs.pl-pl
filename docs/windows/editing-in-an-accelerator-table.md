---
title: Edytowanie w tabeli akceleratora (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
ms.assetid: 545b650b-4f26-4b20-8431-d942548443bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57347b88fe7d54813e06cde6d5f4b3414e79f116
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395813"
---
# <a name="editing-in-an-accelerator-table-c"></a>Edytowanie w tabeli akceleratora (C++)

### <a name="to-edit-in-an-accelerator-table"></a>Edytowanie w tabeli akceleratora

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. Wybierz wpis w tabeli i kliknij, aby aktywować edycji w miejscu.

3. Wybierz z listy rozwijanej kombi lub wpisz w miejscu, aby wprowadzić zmiany.

   - Aby uzyskać [identyfikator](id-property.md), wybierz z listy lub wpisz, aby edytować.

   - Aby uzyskać [modyfikator](../windows/accelerator-modifier-property.md), wybierz z listy.

   - Aby uzyskać [klucz](../windows/accelerator-key-property.md), wybierz z listy lub wpisz, aby edytować.

   - Aby uzyskać [typu](../windows/accelerator-type-property.md), wybierz opcję **ASCII** lub **VIRTKEY** z listy.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytowanie tabel akceleratora](../windows/editing-accelerator-tables.md)<br/>
[Edytor klawiszy skrótów](../windows/accelerator-editor.md)