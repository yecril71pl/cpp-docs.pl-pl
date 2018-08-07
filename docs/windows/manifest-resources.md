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
ms.openlocfilehash: b14684adcefcf975750f64a4a7402083943b9f71
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604085"
---
# <a name="manifest-resources"></a>Zasoby manifestu
Zasoby manifestu są plikami XML, które opisują zależności, których używa aplikacja. Na przykład w programie Visual Studio, plik manifestu generowane przez kreatora MFC definiuje, której wersji 5.0 lub 6.0, Windows formantu typowego bibliotek DLL, należy użyć aplikacji:  
  
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
  
 Dla aplikacji Windows XP lub Windows Vista zasobu manifestu nie tylko określa, że aplikacja używać najnowszej wersji wspólnych formantów Windows (w wersji 6.0, jak pokazano powyżej), ale obsługuje ona również [kontroli Syslink](http://msdn.microsoft.com/library/windows/desktop/bb760706).  
  
 Aby wyświetlić wersję i typ informacji zawartych w zasobu manifestu, można otworzyć pliku w podglądzie XML, lub w programie Visual Studio [edytora tekstów](http://msdn.microsoft.com/508e1f18-99d5-48ad-b5ad-d011b21c6ab1). Aby uzyskać więcej informacji, zobacz [otwarcie zasobu manifestu w edytorze tekstu programu Visual Studio](../windows/how-to-open-a-manifest-resource.md).  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Instruktaż: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
## <a name="limitations"></a>Ograniczenia  
 Może mieć tylko jeden zasób manifestu dla modułu.  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty](../mfc/controls-mfc.md)   
 [Praca z plikami zasobów](../windows/working-with-resource-files.md)