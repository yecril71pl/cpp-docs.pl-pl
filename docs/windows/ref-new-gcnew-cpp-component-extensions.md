---
title: REF new, gcnew (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
dev_langs:
- C++
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 51aec80ee24d96cf08d55778e108492d16ecfcc9
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606188"
---
# <a name="ref-new-gcnew--c-component-extensions"></a>ref new, gcnew (C++ Component Extensions)
**Ref nowe** agregacji — słowo kluczowe przydziela wystąpienie typu, który jest bezużyteczne, gdy obiekt staje się niedostępny, a który zwraca uchwyt ([^](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)) do przydzielonego obiektu.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 Pamięć dla wystąpienia typu, który jest przydzielany przez **ref nowe** jest automatyczne cofnięcie przydziału.  
  
 A **ref nowe** zgłasza operacji `OutOfMemoryException` przypadku nie można przydzielić pamięci.  
  
 Aby uzyskać więcej informacji dotyczących sposobu przydzielone i bez alokacji pamięci dla typów natywnych języka C++, zobacz [nowy i delete — operatory](../cpp/new-and-delete-operators.md).  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Użyj **ref nowe** można przydzielić pamięci dla obiektów środowiska wykonawczego Windows, którego okres istnienia, którą chcesz administrować automatycznie. Obiekt jest automatycznie cofniętą alokacją, gdy jego licznik odwołań zbliża się do zera, która następuje po ostatniej kopii odwołanie stała się poza zakresem. Aby uzyskać więcej informacji, zobacz [klasy i struktury odwołania](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: `/ZW`  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 Pamięć dla typu zarządzanego (odwołania lub typu wartości) została przydzielona przez **gcnew**i za pomocą wyrzucania elementów bezużytecznych z cofniętą alokacją.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: `/clr`  
  
### <a name="examples"></a>Przykłady  
  
 W poniższym przykładzie użyto **gcnew** przydzielić obiektu wiadomości.  
  
```cpp  
// mcppv2_gcnew_1.cpp  
// compile with: /clr  
ref struct Message {  
   System::String^ sender;  
   System::String^ receiver;  
   System::String^ data;  
};  
  
int main() {  
   Message^ h_Message  = gcnew Message;  
  //...  
}  
```  
  
 W poniższym przykładzie użyto **gcnew** utworzyć opakowanym typem wartościowym do użycia, takich jak typ odwołania.  
  
```cpp  
// example2.cpp : main project file.  
// compile with /clr  
using namespace System;  
value class Boxed {  
    public:  
        int i;  
};  
int main()  
{  
    Boxed^ y = gcnew Boxed;  
    y->i = 32;  
    Console::WriteLine(y->i);  
    return 0;  
}  
```  
  
 **Output**  
  
```Output  
32  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)