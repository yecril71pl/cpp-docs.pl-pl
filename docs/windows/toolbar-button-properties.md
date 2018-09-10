---
title: Właściwości przycisku paska narzędzi (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
ms.assetid: b2705814-7c5d-4f24-8f77-07559b0cdda2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b23194992d3b2bb4f1e2708f7e57396cb7e94be6
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318736"
---
# <a name="toolbar-button-properties-c"></a>Właściwości przycisku paska narzędzi (C++)

Właściwości przycisku paska narzędzi są:

|Właściwość|Opis|
|--------------|-----------------|
|**ID**|Określa identyfikator przycisku. Listy rozwijanej udostępnia typowe **identyfikator** nazwy.|
|**Szerokość**|Określa szerokość przycisku. zalecane jest 16 pikseli.|
|**Wysokość**|Określa wysokość przycisku. Należy pamiętać, że wysokość jednego przycisku zmienia się wysokość wszystkie przyciski na pasku narzędzi. Zaleca się 15 pikseli.|
|**wiersz**|Określa komunikat wyświetlany na pasku stanu. Dodawanie \n i nazwę dodaje etykietkę narzędzia do tego przycisku paska narzędzi. Aby uzyskać więcej informacji, zobacz [tworzeniem etykietki narzędzi](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Szerokość** i **wysokość** dotyczą wszystkich przycisków. Mapa bitowa, który jest używany do tworzenia paska narzędzi ma maksymalną szerokość 2048. Dlatego jeśli szerokość przycisku równa 512, może mieć tylko cztery przyciski i jeśli szerokość równa 513, może mieć tylko trzy przyciski.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

ATL i MFC

## <a name="see-also"></a>Zobacz też

[Zmiana właściwości przycisku paska narzędzi](../windows/changing-the-properties-of-a-toolbar-button.md)  
[Edytor paska narzędzi](../windows/toolbar-editor.md)