---
title: Otwieranie zasobów do edycji plików binarnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- binary data, editing
- resources [Visual Studio], opening for binary editing
ms.assetid: d3cdb0e4-da66-410d-8e49-b29073ff2929
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 26d1b0ae8923835b0ce06c7312fa185693c6586e
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014510"
---
# <a name="opening-a-resource-for-binary-editing"></a>Otwieranie zasobów do edycji plików binarnych
### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Aby otworzyć zasób pulpitu Windows do edycji plików binarnych  
  
1.  W [widok zasobów](../windows/resource-view-window.md), wybierz plik określonego zasobu, który chcesz edytować.  
  
    > [!NOTE]
    >  Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Kliknij prawym przyciskiem myszy zasób, a następnie kliknij przycisk **otwartej obsługi danych binarnych** z menu skrótów.  
  
    > [!NOTE]
    >  Jeśli używasz [widok zasobów](../windows/resource-view-window.md) okna, aby otworzyć zasobu w formacie, że Visual Studio nie może rozpoznać (na przykład RCDATA lub zasobów niestandardowych), zasób zostanie automatycznie otwarty w **binarne** edytora.  
  
### <a name="to-open-a-managed-resource-for-binary-editing"></a>Aby otworzyć zarządzanych zasobów do edycji plików binarnych  
  
1.  W **Eksploratora rozwiązań**, wybierz plik określonego zasobu, który chcesz edytować.  
  
2.  Kliknij prawym przyciskiem myszy zasób, a następnie wybierz **Otwórz za pomocą** z menu skrótów.  
  
3.  W **Otwórz za pomocą** okna dialogowego wybierz **Edytor plików binarnych**.  
  
    > [!NOTE]
    >  Możesz użyć [edytora obrazów](../windows/image-editor-for-icons.md) i [edytorze binarnym](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.  
  
    > [!NOTE]
    >  Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).   
  
 ![Edytor plików binarnych](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")  
Dane binarne dla okna dialogowego wyświetlany w edytorze pliku binarnego  
  
 Tylko niektóre wartości ASCII są reprezentowane w edytorze binarnym (0x20 za pośrednictwem 0x7E). Rozszerzone znaki są wyświetlane jako okresy w sekcji wartość ASCII w edytorze binarnym (prawy panel). "Drukowalnych" znaki są wartości ASCII 32 za pośrednictwem 126.  
  
> [!NOTE]
>  Jeśli chcesz używać **binarne** edytora w zasobie już poddane edycji w innym oknie edytora najpierw zamknąć pozostałe okna edytora.  
  
## <a name="requirements"></a>Wymagania  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor plików binarnych](binary-editor.md)