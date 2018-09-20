---
title: Usuwanie wpisu z tabeli akceleratora (C++) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9543f33895e112634bf9c62b00652760313af97f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397198"
---
# <a name="deleting-an-entry-from-an-accelerator-table-c"></a>Usuwanie wpisu z tabeli akceleratora (C++)

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

[Edytowanie tabel akceleratora](../windows/editing-accelerator-tables.md)<br/>
[Edytor klawiszy skrótów](../windows/accelerator-editor.md)