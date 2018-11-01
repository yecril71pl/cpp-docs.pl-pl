---
title: Zmiana właściwości podpisu wielu ciągów zasobów (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- String editor [C++], changing properties of multiple strings
- string tables [C++], changing caption of multiple strings
ms.assetid: 82ac4389-fd9c-4794-a18f-c6bf5b253bd7
ms.openlocfilehash: a0b658684a948bd006c392188ed650756bda297d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530835"
---
# <a name="changing-the-caption-property-of-multiple-string-resources-c"></a>Zmiana właściwości podpisu wielu ciągów zasobów (C++)

Poniższa procedura pokazuje, jak zmienić właściwości podpisu lub wielu ciągów.

### <a name="to-change-the-caption-property-of-multiple-strings"></a>Aby zmienić właściwości podpisu lub wielu ciągów

1. Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. Wybierz parametry, aby zmienić, przytrzymując **Ctrl** klucza podczas klikania każdej z nich.

3. W [okno właściwości](/visualstudio/ide/reference/properties-window), wpisz nową wartość dla właściwości, aby zmienić.

4. Naciśnij klawisz **wprowadź**.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, (te, których platformą docelową środowiska uruchomieniowego języka wspólnego), zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Instruktaż: Lokalizowanie interfejsów Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor ciągów](../windows/string-editor.md)