---
title: Importowanie wywołań funkcji przy użyciu atrybutu __declspec(dllimport)
ms.date: 11/04/2016
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 1743cbba8c3046ef844f16be8e78d43c61f62606
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442522"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>Importowanie wywołań funkcji przy użyciu atrybutu __declspec(dllimport)

Poniższy przykład kodu pokazuje, jak używać **_declspec (dllimport)** do importowania wywołań funkcji z biblioteki DLL do aplikacji. Załóżmy, że `func1` jest funkcją, która znajduje się w bibliotece DLL niezależnie od pliku. exe, który zawiera **główną** funkcję.

Bez **__declspec (dllimport)** , dany kod:

```
int main(void)
{
   func1();
}
```

kompilator generuje kod, który wygląda następująco:

```
call func1
```

a konsolidator tłumaczy wywołanie na coś podobne do tego:

```
call 0x4000000         ; The address of 'func1'.
```

Jeśli `func1` istnieje w innej bibliotece DLL, konsolidator nie może rozwiązać tego problemu bezpośrednio, ponieważ nie ma informacji o tym, co jest adres `func1`. W środowiskach 16-bitowych konsolidator dodaje ten adres kodu do listy w pliku. exe, który zostanie poprawiony przez moduł ładujący w czasie wykonywania z prawidłowym adresem. W środowiskach 32-bitowych i 64-bitowych konsolidator generuje thunk, którego adres jest znany. W środowisku 32-bitowym thunk wygląda następująco:

```
0x40000000:    jmp DWORD PTR __imp_func1
```

W tym miejscu `imp_func1` jest adresem gniazda `func1` w tabeli adresów importu pliku. exe. Wszystkie adresy są w tym przypadku znane dla konsolidatora. Moduł ładujący musi tylko zaktualizować tabelę adresów importu pliku exe w czasie ładowania, aby wszystkie elementy działały prawidłowo.

W związku z tym używanie **__declspec (dllimport)** jest lepszym rozwiązaniem, ponieważ konsolidator nie generuje elementu thunk, jeśli nie jest to wymagane. Sekcje thunk zwiększyć kod (w systemach RISC, może to być kilka instrukcji) i może obniżyć wydajność pamięci podręcznej. Jeśli poinformujesz kompilator, że funkcja znajduje się w bibliotece DLL, może wygenerować pośredniego wywołania.

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

Nie ma żadnych thunk i nie zawiera instrukcji `jmp`, więc kod jest mniejszy i krótszy.

Z drugiej strony, dla wywołań funkcji w bibliotece DLL, nie chcesz używać wywołania pośredniego. Znasz już adres funkcji. Ponieważ czas i miejsce są wymagane do załadowania i zapisania adresu funkcji przed wywołaniem pośrednim, bezpośrednie wywołanie jest zawsze szybsze i mniejsze. Chcesz użyć **__declspec (dllimport)** tylko podczas WYWOŁYWANIA funkcji DLL spoza samego pliku dll. Nie należy używać **__declspec (dllimport)** dla funkcji w bibliotece DLL podczas kompilowania tej biblioteki DLL.

## <a name="see-also"></a>Zobacz też

[Importowanie do aplikacji](importing-into-an-application.md)
