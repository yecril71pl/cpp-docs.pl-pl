---
title: Eksportuj | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.export
dev_langs:
- C++
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ad5f886c4d475cb51b370ae25549387f191ab4b6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39653134"
---
# <a name="export"></a>export
Powoduje to struktura danych, należy umieścić w pliku .idl.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[export]  
```  
  
## <a name="remarks"></a>Uwagi  
 **Wyeksportować** C++ atrybutu powoduje, że struktury danych, można umieścić w pliku .idl i następnie być dostępne w bibliotece typów w formacie zgodnym z pliku binarnego, który sprawia, że dostępne w dowolnym języku.  
  
 Nie można zastosować **wyeksportować** atrybutów do klasy, nawet wtedy, gdy klasa ma tylko publiczne elementy członkowskie (odpowiednik **struktury**).  
  
 Jeśli eksportujesz nienazwane **wyliczenia**s lub **struktury**s, będą one podanej nazwy, które zaczynają się od **__unnamed *** x*, gdzie *x* sekwencyjne numer.  
  
 Definicje typów prawidłowe eksportu są typy podstawowe, struktury, złożenia, wyliczenia lub wpisz identyfikatory.  Zobacz [typedef](http://msdn.microsoft.com/library/windows/desktop/aa367287) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia **wyeksportować** atrybutu:  
  
```cpp  
// cpp_attr_ref_export.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export]  
struct MyStruct {  
   int i;  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|**Unia**, **typedef**, **wyliczenia**, **struktury**, lub **interfejsu**|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty kompilatora](../windows/compiler-attributes.md)   
 [Atrybuty Typedef, Enum, Union oraz Struct](../windows/typedef-enum-union-and-struct-attributes.md)   