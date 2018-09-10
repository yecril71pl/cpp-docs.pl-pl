---
title: Manifest zasobów (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifest resources [C++]
- resources [C++], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6d58e89250708f264ff6bb96c75e8124ffa02509
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316448"
---
# <a name="manifest-resources-c"></a>Zasoby manifestu (C++)

W projektach pulpitu C++ manifestu zasoby są plikami XML, które opisują zależności, których używa aplikacja. Na przykład w programie Visual Studio, plik manifestu generowane przez kreatora MFC definiuje, której wersji 5.0 lub 6.0, Windows formantu typowego bibliotek DLL, należy użyć aplikacji:

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