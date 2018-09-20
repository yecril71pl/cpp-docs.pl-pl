---
title: Połączenie static Const Int nie jest już literałem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- literal attribute [C++]
- constants, declaring
- integral constant expressions
ms.assetid: d2a5e3d2-ffb0-4b61-8114-bec5993a1195
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c51853274b061ba290ff90993f45ccdf3375349b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431297"
---
# <a name="static-const-int-linkage-is-no-longer-literal"></a>Połączenie static const int nie jest już literałem

Deklaracja stałej składowej klasy zmienił się z zarządzanych rozszerzeń języka C++ do Visual C++.

Mimo że `static const` całkowitego elementy członkowskie są nadal obsługiwane, zmieniono jego atrybut powiązania. Atrybut ich wcześniejsze połączenia odbywa się teraz w literału składowej typu całkowitego. Na przykład rozważmy następujące klasy zarządzanych rozszerzeń:

```
public __gc class Constants {
public:
   static const int LOG_DEBUG = 4;
};
```

Spowoduje to wygenerowanie następujących podstawowych atrybutów CIL pola (Uwaga: atrybut literałowy):

```
.field public static literal int32
modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)
```

Gdy to nadal będzie się kompilować w ramach nowej składni:

```
public ref class Constants {
public:
   static const int LOG_DEBUG = 4;
};
```

nie jest już emituje atrybut literałowy, a w związku z tym jest nie wyświetlane jako stała przez środowisko uruchomieniowe CLR:

```
.field public static int32 modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)
```

Aby mogła mieć tego samego atrybutu literałowego między języka, deklaracja powinna zostać zmieniona na nowo obsługiwanych `literal` elementu członkowskiego danych, w następujący sposób,

```
public ref class Constants {
public:
   literal int LOG_DEBUG = 4;
};
```

## <a name="see-also"></a>Zobacz też

[Deklaracje składowych w obrębie klasy lub interfejsu (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[literał](../windows/literal-cpp-component-extensions.md)