---
title: Edytowanie właściwości kontrolki ActiveX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], editing properties
- ActiveX controls [C++], properties
ms.assetid: e5880c62-36c7-4701-bc99-97a82974c22a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e754307c35d10aa36680a42415bd3a5b781321ba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384848"
---
# <a name="editing-properties-for-an-activex-control"></a>Edytowanie właściwości kontrolki ActiveX

Kontrolki ActiveX, dostarczone przez niezależnych dostawców może są wyposażone w ich własnych właściwości i właściwości. Właściwości formantów ActiveX są wyświetlane w **właściwości** okna. Ponadto wszystkie strony właściwości utworzone przez autorów formantu ActiveX są wyświetlane w **strony właściwości** okno dialogowe (Aby wyświetlić **strona właściwości** określonej kontrolki ActiveX, kliknij przycisk  **Strona właściwości** znajdujący się w [okno właściwości](/visualstudio/ide/reference/properties-window)).

Na stronie właściwości dla formantu ActiveX, w zależności od arkuszy właściwości, które pochodzą z formantu ActiveX w ramach będą wyświetlane różne karty.

> [!NOTE]
> Poniższa procedura ma zastosowanie przy użyciu strony właściwości, aby edytować kontrolki ActiveX. Możesz również przeglądać i edytować właściwości formantu ActiveX w nowym **właściwości** okna.

### <a name="to-edit-properties-for-an-activex-control"></a>Aby edytować właściwości kontrolki ActiveX

1. Wybierz **ActiveX** kontroli.

2. Na **widoku** menu, kliknij przycisk **strona właściwości** i Wyświetl właściwości.

3. W razie potrzeby na stronie właściwości, należy wprowadzić zmiany.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Wyświetlanie i dodawanie kontrolek ActiveX do okna dialogowego](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)<br/>
[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)