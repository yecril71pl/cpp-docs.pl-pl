---
title: Wstawianie kontrolki ActiveX, okno dialogowe (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.insertActiveXControls
dev_langs:
- C++
helpviewer_keywords:
- Insert ActiveX Control dialog box [C++]
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: 06638ea3-0726-40da-a989-9b89292d0e3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9a157649f374dfd1fabbecd6ce60523f4208733b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396730"
---
# <a name="insert-activex-control-dialog-box-c"></a>Wstawianie kontrolki ActiveX, okno dialogowe (C++)

To okno dialogowe umożliwia [wstawić formanty ActiveX do dialogowym](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md) podczas korzystania z [Edytor okien dialogowych](../windows/dialog-editor.md).

### <a name="activex-control"></a>Kontrolki ActiveX

Wyświetla listę formantów ActiveX. Wstawianie kontrolki z tego okna dialogowego nie generuje klasę otoki. Klasa otoki, należy użyć [Widok klas](/visualstudio/ide/viewing-the-structure-of-code) ją utworzyć (Aby uzyskać więcej informacji, zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md)). Jeśli formant ActiveX nie ma w tym oknie dialogowym, spróbuj zainstalować kontroli zgodnie z instrukcjami dostawcy.

### <a name="path"></a>Ścieżka

Wyświetla plik, w którym znajduje się Kontrolka ActiveX.

Możesz umieścić formantów w **przybornika** okna, aby mieć łatwy dostęp. Aby uzyskać więcej informacji, zobacz [przybornika](/visualstudio/ide/reference/).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Karta Edytor okien dialogowych, Przybornik](../windows/dialog-editor-tab-toolbox.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)