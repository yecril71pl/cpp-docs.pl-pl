---
title: Zmiana właściwości zasobu ciągu (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource identifiers, string properties
- string tables [C++], changing strings
- strings [C++], properties
ms.assetid: 0a220434-f444-4405-9a64-d28d6b965687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b1fdf47a6995a29641cf18018199f8d7b88a622c
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318359"
---
# <a name="changing-the-properties-of-a-string-resource-c"></a>Zmiana właściwości zasobu ciągu (C++)

### <a name="to-change-a-string-or-its-identifier"></a>Aby zmienić ciąg lub jego identyfikator.

1. Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. Wybierz parametry chcesz edytować, a następnie kliknij dwukrotnie **identyfikator**, **wartość**, lub **podpis** kolumny. Teraz możesz wykonywać następujące czynności:

   - Wybierz **identyfikator** z **identyfikator listy rozwijanej** listy lub wpisz `ID` bezpośrednio w miejscu.

   - Wpisz inny numer w **wartość** kolumny.

   - Typ zmiany w **podpis** kolumny.

        > [!NOTE]
        >  Można również edytować właściwości ciągu w [okno właściwości](/visualstudio/ide/reference/properties-window).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, (te, których platformą docelową środowiska uruchomieniowego języka wspólnego), zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Instruktaż: Lokalizowanie interfejsów Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\)).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor ciągów](../windows/string-editor.md)  