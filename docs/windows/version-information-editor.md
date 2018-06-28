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
ms.openlocfilehash: 76a76dbb3d8b41c2366f354f9c3c8d66ccc3743f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890593"
---
# <a name="version-information-editor"></a>Edytor informacji o wersji
Informacje o wersji składa się z firmy i identyfikator produktu, numer wersji produktu i praw autorskich i znak towarowy powiadomień. W edytorze informacje o wersji można tworzyć i obsługiwać te dane, które są przechowywane w zasobach informacji o wersji. Zasób informacje o wersji nie jest wymagane przez aplikację, ale jest to przydatne miejsce do zbierania informacji, która identyfikuje aplikację. Informacje o wersji jest również używane przez Instalatora interfejsów API.  
  
 Zasobach informacji o wersji ma blok górnym i co najmniej jeden bloków niższe: jeden blok informacji stałej u góry i co najmniej jeden bloków informacyjnych wersji na dole (dla innych języków i/lub zestawów znaków). Górny bloku ma edytowalnego pola liczbowego i wybieranych list rozwijanych. Niższe bloki zawierają tylko pola tekstowe można edytować.  
  
> [!NOTE]
>  Standardowe systemu Windows jest tylko jedna wersja zasobu o nazwie VS_VERSION_INFO.  
  
 Edytor informacji o wersji umożliwia:  
  
-   [Edytowanie ciągu w zasobach informacji o wersji](../windows/editing-a-string-in-a-version-information-resource.md)  
  
-   [Dodaj informacje o wersji dla innego języka (nowy blok informacji o wersji)](../windows/adding-version-information-for-another-language.md)  
  
-   [Usunąć blok informacji o wersji](../windows/deleting-a-version-information-block.md)  
  
-   [Informacje o wersji dostępu w programie](../windows/accessing-version-information-from-within-your-program.md)  
  
    > [!NOTE]
    >  Podczas używania edytora informacje o wersji, w wielu przypadkach należy kliknąć prawym przyciskiem myszy do wyświetlenia menu skrótów poleceń określonych zasobów. Na przykład jeśli klikniesz przycisk podczas wskazuje wpis nagłówek bloku, menu skrótów zawiera polecenia informacji o bloku nowej wersji i usunąć blok informacji o wersji.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytory zasobów](../windows/resource-editors.md)   
 [Menu i innych zasobów](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)

