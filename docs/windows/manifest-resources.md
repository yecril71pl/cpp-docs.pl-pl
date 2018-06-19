---
title: Zasoby manifestu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifest resources
- resources [Visual Studio], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d8df7bf266bae25bd6b898012a6bad10a3d10f81
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882917"
---
# <a name="manifest-resources"></a>Zasoby manifestu
Zasoby manifestu są pliki XML, które opisują zależności, których używa aplikacja. Na przykład w programie Visual Studio pliku manifestu generowane przez kreatora biblioteki MFC definiuje, które z systemu Windows formantu wspólnego bibliotek DLL należy użyć aplikacji, w wersji 5.0 lub 6.0:  
  
```  
<description>Your app description here</description>   
<dependency>   
    <dependentAssembly>   
        <assemblyIdentity   
            type="win32"   
            name="Microsoft.Windows.Common-Controls"   
            version="6.0.0.0"   
            processorArchitecture="X86"   
            publicKeyToken="6595b64144ccf1df"   
            language="*"   
        />   
    </dependentAssembly>   
</dependency>   
```  
  
 W przypadku aplikacji systemu Windows XP lub Windows Vista zasobu manifestu określa nie tylko aplikacji przy użyciu najnowszej wersji formanty standardowe systemu Windows (wersja 6.0, jak pokazano powyżej), ale obsługuje ona również [kontroli Syslink](http://msdn.microsoft.com/library/windows/desktop/bb760706).  
  
 Aby wyświetlić wersję i typ informacji zawartych w zasobu manifestu, można otworzyć pliku w podglądzie XML lub w programie Visual Studio [Edytor tekstu](http://msdn.microsoft.com/en-us/508e1f18-99d5-48ad-b5ad-d011b21c6ab1). Aby uzyskać więcej informacji, zobacz [otwarcie zasobu manifestu w edytorze tekstu Visual Studio](../windows/how-to-open-a-manifest-resource.md).  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [wskazówki: przy użyciu zasobów dla lokalizacji ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
## <a name="limitations"></a>Ograniczenia  
 Może mieć tylko jeden zasób manifestu na moduł.  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty](../mfc/controls-mfc.md)   
 [Praca z plikami zasobów](../windows/working-with-resource-files.md)