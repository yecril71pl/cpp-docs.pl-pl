---
title: Ustawianie szerokości poziomego paska przewijania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls, scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars, displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars, width
ms.assetid: 51dad141-aa0b-46a3-a82c-46b80d603d94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 64dd7bea162839642a10253baddfc7abbe9eb802
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612415"
---
# <a name="setting-the-width-of-a-horizontal-scroll-bar"></a>Ustawianie szerokości poziomego paska przewijania

Po dodaniu pola listy z poziomy pasek przewijania, do okna dialogowego przy użyciu klas MFC pasek przewijania nie będą automatycznie wyświetlane w aplikacji.

### <a name="to-make-the-scroll-bar-appear"></a>Aby wyświetlanie paska przewijania

1. Ustaw maksymalną szerokość elementu najszerszego, wywołując [CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) w kodzie.

   Bez ustawienia tej wartości na pasku przewijania nie będą wyświetlane, nawet jeśli elementy w polu listy są większe niż okno.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

MFC

## <a name="see-also"></a>Zobacz też

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)  
[Kontrolki](../mfc/controls-mfc.md)