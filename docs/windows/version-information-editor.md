---
title: Edytor informacji o wersji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version.F1
dev_langs:
- C++
helpviewer_keywords:
- Version Information editor, about Version Information editor
- editors, Version Information
- resource editors, Version Information editor
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a8ea040d5a549c61ba17f059260cb399d82bc430
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013970"
---
# <a name="version-information-editor"></a>Edytor informacji o wersji
Informacje o wersji składa się z firmy i identyfikacji produktu, numer wersji produktu i praw autorskich i znak towarowy powiadomień. Za pomocą **informacje o wersji** edytora, możesz tworzyć i obsługiwać te dane, które jest przechowywane w zasobach informacji o wersji. Zasobach informacji o wersji nie jest wymagane przez aplikację, ale jest użytecznym miejscem, aby zebrać informacje identyfikujące aplikację. Informacje o wersji jest również używany przez Instalatora interfejsów API.  
  
 Zasobach informacji o wersji ma blokiem górnej i jeden lub więcej bloków niższe: jeden blok informacji stałej u góry i jeden lub więcej bloków informacyjnych wersji u dołu (w przypadku innych języków i/lub zestawów znaków). Blokuj najważniejsze ma edytowalnych pól liczbowych i list rozwijanych można wybrać. Niższe bloki zawierają tylko edytowalnymi polami tekstowymi.  
  
> [!NOTE]
>  Standardowa Windows jest tylko jedna wersja zasobu o nazwie VS_VERSION_INFO.  
  
 **Informacje o wersji** Edytor umożliwia:  
  
-   [Edytowanie ciągu w zasobach informacji o wersji](../windows/editing-a-string-in-a-version-information-resource.md)  
  
-   [Dodaj informacje o wersji dla innego języka (nowej wersję bloku informacyjnego)](../windows/adding-version-information-for-another-language.md)  
  
-   [Usuwanie bloku informacji o wersji](../windows/deleting-a-version-information-block.md)  
  
-   [Informacje o wersji dostęp z Twojego programu](../windows/accessing-version-information-from-within-your-program.md)  
  
    > [!NOTE]
    >  Podczas korzystania z **informacje o wersji** edytora w wielu przypadkach, kliknięcie prawym przyciskiem myszy, aby wyświetlić menu skrótów poleceń specyficznych dla zasobów. Na przykład jeśli klikniesz podczas wskazujący wpis nagłówka bloku pokazuje menu skrótów **nowe informacje o bloku wersji** i **usuwanie bloku informacji o wersji** poleceń.  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytory zasobów](../windows/resource-editors.md)   
 [Menu i inne zasoby](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)