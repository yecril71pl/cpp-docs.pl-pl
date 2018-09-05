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
ms.openlocfilehash: 0f06e2d430867d04600547312fbc484ec6257c53
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685155"
---
# <a name="manifest-resources"></a>Zasoby manifestu

Zasoby manifestu są plikami XML, które opisują zależności, których używa aplikacja. Na przykład w programie Visual Studio, plik manifestu generowane przez kreatora MFC definiuje, której wersji 5.0 lub 6.0, Windows formantu typowego bibliotek DLL, należy użyć aplikacji:

```xml
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

Dla aplikacji Windows XP lub Windows Vista zasobu manifestu nie tylko określa, że aplikacja używać najnowszej wersji wspólnych formantów Windows (w wersji 6.0, jak pokazano powyżej), ale obsługuje ona również [kontroli Syslink](/windows/desktop/Controls/syslink-overview).

Aby wyświetlić wersję i typ informacji zawartych w zasobu manifestu, można otworzyć go w podglądzie XML lub Edytor tekstu Visual Studio. Aby uzyskać więcej informacji, zobacz [otwarcie zasobu manifestu w edytorze tekstu programu Visual Studio](../windows/how-to-open-a-manifest-resource.md).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*.

## <a name="limitations"></a>Ograniczenia

Może mieć tylko jeden zasób manifestu dla modułu.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki](../mfc/controls-mfc.md)  
[Praca z plikami zasobów](../windows/working-with-resource-files.md)