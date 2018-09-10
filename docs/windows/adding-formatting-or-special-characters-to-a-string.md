---
title: Dodawanie znaków specjalnych ani formatowania do zasobu ciągu (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: c40f394a-8b2c-4896-ab30-6922863ddbb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8bf67723f516e0c5b1bf9931d7f53d36907fca86
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313393"
---
# <a name="adding-formatting-or-special-characters-to-a-string-resource-c"></a>Dodawanie znaków specjalnych ani formatowania do zasobu ciągu (C++)

### <a name="to-add-formatting-or-special-characters-to-a-string"></a>Aby dodać znaków specjalnych ani formatowania na ciąg

1. Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. Wybierz ciąg, który chcesz zmodyfikować.

3. W [okno właściwości](/visualstudio/ide/reference/properties-window), Dodaj dowolne sekwencje unikowe standardowych wymienionych poniżej, aby tekst w **podpis** pole i naciśnij klawisz **Enter**.

   |Aby uzyskać dostęp do tej|Wpisz to|
   |-----------------|---------------|
   |Nowy wiersz|\n|
   |Powrót karetki|\r|
   |Tab|\t|
   |Ukośnik odwrotny (\\)|\\\|
   |Znak ASCII|\ddd (Zapis ósemkowy)|
   |alert (dzwonek)|\a|

> [!NOTE]
> **Ciąg** edytor nie obsługuje pełny zestaw znaki ucieczki przestają być ASCI. Można używać tylko wymienione powyżej.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, (te, których platformą docelową środowiska uruchomieniowego języka wspólnego), zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Instruktaż: Lokalizowanie interfejsów Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3\(v=vs.100\)).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor ciągów](../windows/string-editor.md)  