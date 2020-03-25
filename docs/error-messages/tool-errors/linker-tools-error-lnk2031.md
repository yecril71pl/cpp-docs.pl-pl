---
title: Błąd narzędzi konsolidatora LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 096ccb7ff443d24e0d53e73a5950faa1e85aeae6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194567"
---
# <a name="linker-tools-error-lnk2031"></a>Błąd narzędzi konsolidatora LNK2031

> nie można wygenerować elementu p/Invoke dla "*function_declaration*" *decorated_name*; Brak konwencji wywoływania w metadanych

## <a name="remarks"></a>Uwagi

Podczas próby zaimportowania funkcji natywnej do czystego obrazu należy pamiętać, że niejawne konwencje wywoływania różnią się między natywnymi i czystymi kompilacjami. Aby uzyskać więcej informacji o czystych obrazach, zobacz [czysty iC++możliwy do zweryfikowania kod (/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

**/CLR: Pure** kompilator Option jest przestarzały w programie visual Studio 2015 i nieobsługiwany w programie visual Studio 2017.

## <a name="example"></a>Przykład

Ten przykładowy kod generuje składnik z wyeksportowaną, natywną funkcją, której Konwencja wywołania jest niejawnie [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>Przykład

Poniższy przykład tworzy czysty klient korzystający z funkcji natywnej. Jednakże Konwencja wywoływania w opcji **/CLR: Pure** jest [__clrcall](../../cpp/clrcall.md). Poniższy przykład generuje LNK2031.

```cpp
// LNK2031_b.cpp
// compile with: /clr:pure LNK2031.lib
// LNK2031 expected
extern "C" int func();

int main() {
   return func();
}
```

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać funkcji natywnej z czystego obrazu. Zanotuj jawny specyfikator konwencji wywoływania **__cdecl** .

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```
