---
title: Okno dialogowe Nowy zasób paska narzędzi (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.newtoolbarresource
dev_langs:
- C++
helpviewer_keywords:
- New Toolbar Resource dialog box [C++]
ms.assetid: 52dd01ad-e748-4ab2-b3eb-59f5df990ca6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ca09463a2934db0097c09d6a4f928f108fd0760
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316305"
---
# <a name="new-toolbar-resource-dialog-box-c"></a>Okno dialogowe Nowy zasób paska narzędzi (C++)

**Nowy zasób paska narzędzi** okno dialogowe umożliwia określenie szerokości i wysokości przycisków, które dodajesz do zasobu paska narzędzi w projekcie C++. Wartość domyślna to 16 x 15 pikseli.

Mapa bitowa, który jest używany do tworzenia paska narzędzi ma maksymalną szerokość 2048. Jeśli ustawisz **szerokość przycisku** do 512, możesz mieć tylko cztery przyciski. Ustaw szerokość 513, może mieć tylko trzy przyciski.

### <a name="button-width"></a>Szerokość przycisku.

Miejsce na wprowadź szerokość przycisków paska narzędzi, konwertowany z zasobu mapy bitowej do zasobu paska narzędzi. Obrazy są obcinane do szerokości i wysokości określone i kolory są dostosowane by wykorzystywały standardowe kolory paska narzędzi (16 kolorów).

### <a name="button-height"></a>Wysokość przycisku

Miejsce na Wprowadź wysokość przycisków paska narzędzi, konwertowany z zasobu mapy bitowej do zasobu paska narzędzi. Obrazy są obcinane do szerokości i wysokości określone i kolory są dostosowane by wykorzystywały standardowe kolory paska narzędzi (16 kolorów).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

ATL i MFC

## <a name="see-also"></a>Zobacz też

[Właściwości przycisku paska narzędzi](../windows/toolbar-button-properties.md)  
[Konwertowanie map bitowych na paski narzędzi](../windows/converting-bitmaps-to-toolbars.md)  
[Edytor paska narzędzi](../windows/toolbar-editor.md)