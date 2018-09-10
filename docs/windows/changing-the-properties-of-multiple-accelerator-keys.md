---
title: Zmiana właściwości kilku klawiszy skrótów (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bf70622dc901842a74cf8718d9447f899defb57d
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313523"
---
# <a name="changing-the-properties-of-multiple-accelerator-keys-c"></a>Zmiana właściwości kilku klawiszy skrótów (C++)

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Aby zmienić właściwości kilku klawiszy skrótów

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. Wybierz klawisze skrótów chcesz zmienić, przytrzymując **Ctrl** klucza podczas klikania każdej z nich.

3. Przejdź do [okno właściwości](/visualstudio/ide/reference/properties-window) i wpisz wartości, które mają wszystkich wybranych akceleratorów, aby udostępnić.

   > [!NOTE]
   > Każda wartość modyfikator jest wyświetlana jako właściwość typu Boolean w **właściwości** okna. Jeśli zmienisz [modyfikator](../windows/accelerator-modifier-property.md) wartość w **właściwości** oknie tabeli akceleratora traktuje nowy modyfikator jako dodatek do wszelkich modyfikatorów, które były wcześniej dostępne. W związku z tym Jeśli ustawisz wartości modyfikatora będzie należy ustawić wszystkie z nich, aby upewnić się, że każdy akcelerator udostępnia takie same **modyfikator** ustawienia.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytowanie tabel akceleratora](../windows/editing-accelerator-tables.md)  
[Edytor klawiszy skrótów](../windows/accelerator-editor.md)