---
title: Kontrolki niestandardowe w edytorze okien dialogowych (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- Custom Control
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], templates
- custom controls [C++], dialog boxes
- custom controls [C++]
- dialog box controls [C++], custom (user) controls
- Dialog Editor [C++], custom controls
ms.assetid: f494b314-4000-4bbe-bbd0-4b18fb71ede1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9ae41727caedfaf09ac5f312ea4d794398cb572c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383431"
---
# <a name="custom-controls-in-the-dialog-editor-c"></a>Kontrolki niestandardowe w edytorze okien dialogowych (C++)

Edytor okien dialogowych pozwala Użyj istniejącej "niestandardowe" lub "user" kontrolek w szablonu okna dialogowego.

> [!NOTE]
> Niestandardowe formanty w tym sensie są nie należy mylić z kontrolkami ActiveX. Kontrolki ActiveX były nazywane niestandardowych formantów OLE. Ponadto nie należy mylić tych kontrolek z kontrolki rysowane przez właściciela z Windows.

Ta funkcja jest przeznaczona do umożliwiają używanie kontrolek w inne niż te dostarczone przez Windows. W czasie wykonywania kontrolka jest skojarzony z klasy okna (nie taka sama jak klasa C++). Jest bardziej typowym sposobem wykonania tego samego zadania do zainstalowania dowolnej kontrolki, takie jak formant statyczny w oknie dialogowym. Następnie w czasie wykonywania w [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkcji, Usuń tę kontrolkę i zastąp go własny niestandardowy formant.

Jest to technika stary. Obecnie zaleca w większości przypadków można zapisać formantu ActiveX lub podklasy formantu wspólnego Windows.

W przypadku kontrolek niestandardowych są ograniczone do:

- Ustawianie lokalizacji w oknie dialogowym.

- Wpisywanie podpisu.

- Identyfikowanie nazwę klasy Windows formantu (kod aplikacji należy go zarejestrować przy użyciu tej nazwy).

- Wpisując wartość szesnastkową 32-bitowe i ustawia styl formantu.

- Ustawianie rozszerzonego stylu.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)