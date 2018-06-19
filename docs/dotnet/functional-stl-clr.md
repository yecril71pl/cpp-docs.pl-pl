---
title: funkcjonalności (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/functional>
dev_langs:
- C++
helpviewer_keywords:
- <functional> header [STL/CLR]
- <cliext/functional> header [STL/CLR]
- functional functions [STL/CLR]
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 38bfbe025c92aa54956a165367b367cecc6160b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112839"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)
Dołącz nagłówek STL/CLR `<cliext/functional>` do definiowania liczba szablonu klasy i delegaci pokrewne szablonu i funkcje.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <functional>  
```  
  
## <a name="declarations"></a>Deklaracje  
  
|Delegate|Opis|  
|--------------|-----------------|  
|[binary_delegate (STL/CLR)](../dotnet/binary-delegate-stl-clr.md)|Delegat dwóch argumentów.|  
|[binary_delegate_noreturn (STL/CLR)](../dotnet/binary-delegate-noreturn-stl-clr.md)|Zwracanie delegata dwuargumentowej `void`.|  
|[unary_delegate (STL/CLR)](../dotnet/unary-delegate-stl-clr.md)|Delegat jeden argument.|  
|[unary_delegate_noreturn (STL/CLR)](../dotnet/unary-delegate-noreturn-stl-clr.md)|Zwraca delegata jeden argument `void`.|  
  
|Class|Opis|  
|-----------|-----------------|  
|[binary_negate (STL/CLR)](../dotnet/binary-negate-stl-clr.md)|Obiekt, aby odwrócić obiekt dwóch argumentów.|  
|[binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)|Obiekt, aby powiązać pierwszy argument obiekt dwóch argumentów.|  
|[binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)|Obiekt powiązać drugi argument obiekt dwóch argumentów.|  
|[divides (STL/CLR)](../dotnet/divides-stl-clr.md)|Podziel obiekt.|  
|[equal_to (STL/CLR)](../dotnet/equal-to-stl-clr.md)|Obiekt do porównania takie same.|  
|[greater (STL/CLR)](../dotnet/greater-stl-clr.md)|Większa obiekt do porównania.|  
|[greater_equal (STL/CLR)](../dotnet/greater-equal-stl-clr.md)|Obiekt większy lub równy porównania.|  
|[less (STL/CLR)](../dotnet/less-stl-clr.md)|Mniej obiekt do porównania.|  
|[less_equal (STL/CLR)](../dotnet/less-equal-stl-clr.md)|Obiekt mniejsza lub równa porównania.|  
|[logical_and (STL/CLR)](../dotnet/logical-and-stl-clr.md)|Obiekt i logicznych.|  
|[logical_not (STL/CLR)](../dotnet/logical-not-stl-clr.md)|Logiczna nie obiekt.|  
|[logical_or (STL/CLR)](../dotnet/logical-or-stl-clr.md)|Obiekt lub logiczne.|  
|[minus (STL/CLR)](../dotnet/minus-stl-clr.md)|Odejmowanie obiekt.|  
|[modulus (STL/CLR)](../dotnet/modulus-stl-clr.md)|Obiekt moduł.|  
|[multiplies (STL/CLR)](../dotnet/multiplies-stl-clr.md)|Należy pomnożyć obiekt.|  
|[negate (STL/CLR)](../dotnet/negate-stl-clr.md)|Obiekt do zwrócenia jej argument zanegowane.|  
|[not_equal_to (STL/CLR)](../dotnet/not-equal-to-stl-clr.md)|Obiekt nie równa porównania.|  
|[plus (STL/CLR)](../dotnet/plus-stl-clr.md)|Dodaj obiekt.|  
|[unary_negate (STL/CLR)](../dotnet/unary-negate-stl-clr.md)|Obiekt, aby odwrócić obiekt jeden argument.|  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[bind1st (STL/CLR)](../dotnet/bind1st-stl-clr.md)|Generuje binder1st — argument i obiekt.|  
|[bind2nd (STL/CLR)](../dotnet/bind2nd-stl-clr.md)|Generuje binder2nd — argument i obiekt.|  
|[not1 (STL/CLR)](../dotnet/not1-stl-clr.md)|Generuje unary_negate — dla obiekt.|  
|[not1 (STL/CLR)](../dotnet/not1-stl-clr.md)|Generuje binary_negate — dla obiekt.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/funkcjonalności >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)