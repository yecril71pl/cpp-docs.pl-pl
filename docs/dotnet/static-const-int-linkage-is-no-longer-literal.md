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
ms.openlocfilehash: cc3f72080c08807026c6458979ac0ba561e298df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164999"
---
# <a name="static-const-int-linkage-is-no-longer-literal"></a>Połączenie static const int nie jest już literałem
Deklaracja stałej elementu członkowskiego klasy zmienił się z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 Mimo że `static const` integralną elementy członkowskie są nadal obsługiwane, ich atrybut powiązania został zmieniony. Atrybut ich wcześniejsze połączenie odbywa się teraz w elemencie członkowskim integralną literału. Na przykład wziąć pod uwagę następujące klasy rozszerzeń zarządzanych:  
  
```  
public __gc class Constants {  
public:  
   static const int LOG_DEBUG = 4;  
};  
```  
  
 Powoduje to następujące atrybuty CIL podstawowej dla pola (Uwaga atrybutu literałowego):  
  
```  
.field public static literal int32   
modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)  
```  
  
 Gdy to nadal kompiluje w nowej składni:  
  
```  
public ref class Constants {  
public:  
   static const int LOG_DEBUG = 4;  
};  
```  
  
 już nie emituje atrybut literałowy, a w związku z tym nie wyświetlania jako stała przez środowisko uruchomieniowe CLR:  
  
```  
.field public static int32 modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier) STANDARD_CLIENT_PRX = int32(0x00000004)  
```  
  
 Aby przypisać tego samego atrybutu literałowego między języka, można zmienić deklaracji do nowo obsługiwanych `literal` element członkowski danych w następujący sposób,  
  
```  
public ref class Constants {  
public:  
   literal int LOG_DEBUG = 4;  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje członków w obrębie klasy lub interfejsu (C + +/ CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [Literału](../windows/literal-cpp-component-extensions.md)