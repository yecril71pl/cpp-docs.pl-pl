---
title: Importowanie wywołań funkcji przy użyciu atrybutu __declspec(dllimport)
description: Jak i dlaczego należy używać __declspec (dllimport) podczas wywoływania danych i funkcji biblioteki DLL.
ms.date: 05/03/2020
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 515fbdb2824c1eaf41e822adeae1a16d3072eec4
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765724"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>Importowanie wywołań funkcji przy użyciu`__declspec(dllimport)`

Dodawanie adnotacji do wywołań przy **`__declspec(dllimport)`** użyciu programu może zwiększyć ich szybkość. **`__declspec(dllimport)`** jest zawsze wymagane w celu uzyskania dostępu do wyeksportowanych danych DLL.

## <a name="import-a-function-from-a-dll"></a>Importowanie funkcji z biblioteki DLL

Poniższy przykład kodu pokazuje, jak używać **`__declspec(dllimport)`** do importowania wywołań funkcji z biblioteki DLL do aplikacji. Załóżmy, `func1` że jest funkcją, która znajduje się w bibliotece DLL niezależnie od pliku wykonywalnego, który zawiera **główną** funkcję.

Bez **`__declspec(dllimport)`**, pod tym kodem:

```C
int main(void)
{
   func1();
}
```

kompilator generuje kod, który wygląda następująco:

```asm
call func1
```

a konsolidator tłumaczy wywołanie na coś podobne do tego:

```asm
call 0x4000000         ; The address of 'func1'.
```

Jeśli `func1` istnieje w innej bibliotece DLL, konsolidator nie może rozpoznać tego adresu bezpośrednio, ponieważ nie ma on informacji o tym, czym `func1` jest adres. W środowiskach 32-bitowych i 64-bitowych konsolidator generuje thunk o znanym adresie. W środowisku 32-bitowym thunk wygląda następująco:

```asm
0x40000000:    jmp DWORD PTR __imp_func1
```

Poniżej `__imp_func1` znajduje się adres `func1` miejsca w tabeli adresów importu pliku wykonywalnego. Wszystkie te adresy są znane dla konsolidatora. Moduł ładujący musi tylko zaktualizować tabelę adresów importu pliku wykonywalnego w czasie ładowania, aby wszystkie elementy działały prawidłowo.

To dlatego, że **`__declspec(dllimport)`** użycie jest lepsze: ponieważ konsolidator nie generuje elementu thunk, jeśli nie jest to wymagane. Sekcje thunk zwiększyć kod (w systemach RISC, może to być kilka instrukcji) i może obniżyć wydajność pamięci podręcznej. Jeśli poinformujesz kompilator, że funkcja znajduje się w bibliotece DLL, może wygenerować pośredniego wywołania.

Teraz ten kod:

```C
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

generuje tę instrukcję:

```asm
call DWORD PTR __imp_func1
```

Nie istnieje thunk i brak `jmp` instrukcji, więc kod jest mniejszy i krótszy. Ten sam efekt można również uzyskać bez **`__declspec(dllimport)`** użycia funkcji optymalizacji całego programu. Aby uzyskać więcej informacji, zobacz [/GL (Optymalizacja całego programu)](reference/gl-whole-program-optimization.md).

W przypadku wywołań funkcji w bibliotece DLL nie trzeba używać wywołania pośredniego. Konsolidator zna już adres funkcji. Ładowanie i przechowywanie adresu funkcji przed pośrednim wywołaniem zajmuje dodatkowy czas i miejsce. Bezpośrednie wywołanie jest zawsze szybsze i mniejsze. Chcesz użyć **`__declspec(dllimport)`** tylko podczas WYWOŁYWANIA funkcji DLL spoza samego pliku dll. Podczas kompilowania tej biblioteki DLL nie należy używać **`__declspec(dllimport)`** funkcji w ramach biblioteki DLL.

## <a name="see-also"></a>Zobacz także

[Importowanie do aplikacji](importing-into-an-application.md)
