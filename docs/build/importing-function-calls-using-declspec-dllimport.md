---
title: Importowanie wywołań funkcji przy użyciu atrybutu __declspec(dllimport) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- __declspec
- dllimport
dev_langs:
- C++
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3f7c1bf81b94eebbe32b40053fc5ce3aeaa0bd7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715796"
---
# <a name="importing-function-calls-using-declspecdllimport"></a>Importowanie wywołań funkcji przy użyciu atrybutu __declspec(dllimport)

Poniższy przykład kodu pokazuje sposób użycia **_declspec(dllimport)** importowanie wywołań funkcji z biblioteki DLL do aplikacji. Przyjęto założenie, że `func1` jest funkcją, która znajduje się w bibliotece DLL, które są niezależne od pliku .exe, który zawiera **głównego** funkcji.

Bez **__declspec(dllimport)**, biorąc pod uwagę ten kod:

```
int main(void)
{
   func1();
}
```

Kompilator generuje kod, który wygląda w następujący sposób:

```
call func1
```

i konsolidator tłumaczy wywołanie na podobny do poniższego:

```
call 0x4000000         ; The address of 'func1'.
```

Jeśli `func1` istnieje w innej bibliotece DLL, konsolidator nie może rozpoznać on bezpośrednio, ponieważ ma ona żadnej możliwość określenia jakiego adresu `func1` jest. W środowiskach 16-bitowych konsolidator dodaje ten kod adres do listy w pliku .exe, który moduł ładujący będzie poprawki w czasie wykonywania na prawidłowy adres. W 32-bitowych i 64-bitowego środowiska konsolidator generuje thunk, które znasz adresu. W środowisku 32-bitowych thunk wygląda następująco:

```
0x40000000:    jmp DWORD PTR __imp_func1
```

W tym miejscu `imp_func1` adres `func1` gniazdo w tabeli adresów importowania pliku .exe. Wszystkie adresy dlatego są znane do konsolidatora. Moduł ładujący ma tylko można zaktualizować tabeli adresów importowania pliku .exe w czasie ładowania wszystko działało poprawnie.

W związku z tym, za pomocą **__declspec(dllimport)** jest lepsza, ponieważ konsolidator nie generuje sekcją thunk, jeśli nie jest wymagana. Sekcje Thunk powiększyć kodu (w systemach RISC, może być kilka instrukcji) i może zmniejszyć wydajność pamięci podręcznej. Jeśli kompilator jest stwierdzić, że funkcja znajduje się w bibliotece DLL, może generować wywołanie pośrednie dla Ciebie.

Teraz ten kod:

```
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

generuje tę instrukcję:

```
call DWORD PTR __imp_func1
```

Istnieje nie thunk i nie `jmp` instrukcji, dzięki czemu kod jest mniejsze i szybsze.

Z drugiej strony dla wywołań funkcji wewnątrz biblioteki DLL, nie będzie ma być konieczne użycie wywołanie pośrednie. Znasz już adresu funkcji. Ponieważ czas i miejsce są wymagane do ładowania i przechowywania adresu funkcji przed wywołanie pośrednie, bezpośrednie wywołanie jest zawsze szybszy i mniejszy. Chcesz użyć **__declspec(dllimport)** podczas wywoływania funkcji DLL z poza bibliotekę DLL, sam. Nie używaj **__declspec(dllimport)** funkcji wewnątrz biblioteki DLL, podczas tworzenia tej biblioteki DLL.

## <a name="see-also"></a>Zobacz też

[Importowanie do aplikacji](../build/importing-into-an-application.md)