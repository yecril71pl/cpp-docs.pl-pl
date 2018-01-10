---
title: emitidl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.emitidl
dev_langs: C++
helpviewer_keywords: emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 55fc74eef3d2ead7312f7dca46f20c3a1ed7ba91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="emitidl"></a>emitidl
Określa, czy wszystkie atrybuty IDL kolejne są przetwarzane i umieszczony w pliku .idl wygenerowany.  
  
## <a name="syntax"></a>Składnia  
  
```
[ emitidl(state, defaultimports=boolean) ];
```  
  
### <a name="parameters"></a>Parametry  
*Stan*  
Jedną z następujących wartości: **true**, **false**, **wymuszone**, **ograniczeniami**, **wypychania**, lub **pop**.  
  
-   Jeśli **true**, wszystkie atrybuty kategorii IDL w pliku kodu źródłowego są umieszczane w pliku .idl wygenerowany. Jest to domyślne ustawienie dla **emitidl**.  
  
-   Jeśli **false**, wszystkie atrybuty kategorii IDL w pliku kodu źródłowego nie są umieszczane w pliku .idl wygenerowany.  
  
-   Jeśli **ograniczeniami**, umożliwia atrybuty IDL w pliku bez [modułu](../windows/module-cpp.md) atrybutu. Kompilator nie generuje pliku .idl.  
  
-   Jeśli **wymuszone**, zastępuje kolejnej **ograniczeniami** atrybut, który wymaga pliku ma **modułu** atrybut, jeśli istnieją IDL atrybutów w pliku.  
  
-   **wypychania** umożliwia zapisanie bieżącego **emitidl** ustawienia do wewnętrznego **emitidl** stosu i **pop** umożliwia ustawisz **emitidl**niezależnie od wartości jest na początku wewnętrznej **emitidl** stosu.  
  
`defaultimports=`*wartość logiczna* \(opcjonalne)  
-   Jeśli *logiczna* jest **true**, docobj.idl jest importowany do pliku .idl wygenerowany. Ponadto jeśli plik o takiej samej nazwie jak .h pliku .idl, który `#include` w źródle kod znajduje się w tym samym katalogu co plik .h, a następnie pliku .idl wygenerowanego zawiera instrukcję import dla tego pliku .idl.  
  
-   Jeśli *logiczna* jest **false**, docobj.idl nie jest importowany do pliku .idl wygenerowany. .Idl — pliki z jawnie należy zaimportować [zaimportować](../windows/import.md).  
  
## <a name="remarks"></a>Uwagi  
Po **emitidl** napotkano atrybut C++ w pliku kodu źródłowego, atrybuty IDL kategorii są umieszczane w pliku .idl wygenerowany. W przypadku nie **emitidl** , atrybuty IDL w pliku kodu źródłowego są dane wyjściowe do pliku .idl wygenerowany.  
  
Użytkownik może mieć wielu **emitidl** atrybutów w pliku kodu źródłowego. Jeśli `[emitidl(false)];` napotkano w pliku bez dalszej `[emitidl(true)];`, a następnie atrybuty nie są przetwarzane w pliku .idl wygenerowany.  
  
Zawsze kompilator napotka nowy plik **emitidl** niejawnie ustawiono **true**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Dowolnego miejsca|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
[Atrybuty kompilatora](../windows/compiler-attributes.md)   
[Oddzielne atrybuty](../windows/stand-alone-attributes.md)   
[Przykłady atrybutów](http://msdn.microsoft.com/en-us/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)