---
title: Usuwanie wpisu z tabeli akceleratora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], deleting entries
- keyboard shortcuts [C++], deleting entry from accelerator table
ms.assetid: cc9cd499-dc04-4fe6-9393-a3e471e115a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0c191a2e37e4fe99c12486270c34a558cf4e8455
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605410"
---
# <a name="deleting-an-entry-from-an-accelerator-table"></a>Usuwanie wpisu z tabeli akceleratora

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>Aby usunąć wpis z tabeli akceleratora

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. Wybierz wpis, który chcesz usunąć. (Naciśnij i przytrzymaj **Ctrl** lub **Shift** klucza podczas klikania, aby wybrać wiele wpisów.)

3. Kliknij prawym przyciskiem myszy i wybierz polecenie **Usuń** z menu skrótów (lub wybierz **Usuń** z **Edytuj** menu).

\- lub —

- Naciśnij klawisz **Usuń** klucza.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytowanie tabel akceleratora](../windows/editing-accelerator-tables.md)  
[Edytor klawiszy skrótów](../windows/accelerator-editor.md)