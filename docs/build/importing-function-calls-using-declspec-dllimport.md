---
title: "Importowanie wywołań funkcji przy użyciu atrybutu __declspec(dllimport) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __declspec
- dllimport
dev_langs: C++
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d1501506d4575c5f7fe1ff1dc7823cbd1545b974
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="importing-function-calls-using-declspecdllimport"></a>Importowanie wywołań funkcji przy użyciu atrybutu __declspec(dllimport)
Poniższy przykładowy kod przedstawia sposób użycia **_declspec(dllimport)** do importowania wywołania funkcji z biblioteki DLL do aplikacji. Przyjęto założenie, że `func1` jest funkcją, która znajduje się w bibliotece DLL niezależnie od pliku .exe, który zawiera **głównego** funkcji.  
  
 Bez **__declspec(dllimport)**, podane ten kod:  
  
```  
int main(void)   
{  
   func1();  
}  
```  
  
 Kompilator generuje kod, który wygląda następująco:  
  
```  
call func1  
```  
  
 i konsolidator tłumaczy wywołanie na podobny do następującego:  
  
```  
call 0x4000000         ; The address of 'func1'.  
```  
  
 Jeśli `func1` istnieje w innej bibliotece DLL, konsolidator nie można rozpoznać tego bezpośrednio, ponieważ go nie ma możliwości otrzymuje żadnej informacji o jakie adres `func1` jest. W środowiskach 16-bitowych konsolidator dodaje ten kod adres do listy w pliku .exe, który moduł ładujący może zastosować poprawki w czasie wykonywania z poprawnym adresem. W środowiskach 32-bitowe i 64-bitowych konsolidator generuje thunk, z których znać adres. W 32-bitowego środowiska thunk wygląda następująco:  
  
```  
0x40000000:    jmp DWORD PTR __imp_func1  
```  
  
 W tym miejscu `imp_func1` adres `func1` gniazda tabelę adresów importu pliku .exe. Wszystkie adresy w związku z tym wiadomo, że konsolidator. Moduł ładujący ma tylko zaktualizować tabelę adresów importu pliku .exe w czasie ładowania dla wszystkie informacje niezbędne do prawidłowego działania.  
  
 W związku z tym przy użyciu **__declspec(dllimport)** jest lepszym rozwiązaniem, ponieważ konsolidator nie generuje thunk, jeśli nie jest wymagana. Sekcje Thunk powiększyć kodu (w systemach RISC, może być kilka instrukcje) i może zmniejszyć wydajność pamięci podręcznej. Jeśli nakazuje kompilatorowi się, że funkcja jest w bibliotece DLL, może generować wywołanie pośrednie dla Ciebie.  
  
 Dlatego teraz ten kod:  
  
```  
__declspec(dllimport) void func1(void);  
int main(void)   
{  
   func1();  
}  
```  
  
 generuje tej instrukcji:  
  
```  
call DWORD PTR __imp_func1  
```  
  
 Brak nie thunk i nie `jmp` instrukcji, dzięki czemu kod jest szybsze i mniejsze.  
  
 Z drugiej strony dla wywołania funkcji wewnątrz biblioteki DLL, nie ma zostać umożliwia wywołanie pośrednie. Znasz już adresu funkcji. Ponieważ obciążenia i przechowywać adresu funkcji przed pośrednie wywołanie wymaga czasu i miejsca, bezpośrednie wywołanie jest zawsze szybsze i mniejsze. Chcesz użyć **__declspec(dllimport)** podczas wywoływania funkcji DLL z poza biblioteki DLL, do samej siebie. Nie używaj **__declspec(dllimport)** funkcji wewnątrz bibliotekę DLL, podczas tworzenia tej biblioteki DLL.  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie do aplikacji](../build/importing-into-an-application.md)