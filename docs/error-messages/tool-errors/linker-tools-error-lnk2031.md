---
title: Błąd narzędzi konsolidatora LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 003b9a58bfb08130f034530f59e2de27efa2ae8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484845"
---
# <a name="linker-tools-error-lnk2031"></a>Błąd narzędzi konsolidatora LNK2031

> Nie można wygenerować p/invoke do "*function_declaration*" *decorated_name*; Brak metadanych konwencji wywoływania

## <a name="remarks"></a>Uwagi

Podczas próby zaimportowania funkcji natywnej do czystego obrazu, należy pamiętać, że niejawne konwencji wywoływania różnią się macierzystych i czystych kompilacji. Aby uzyskać więcej informacji o obrazach czystego, zobacz [czystej i możliwe do zweryfikowania kodu (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

**/CLR: pure** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

## <a name="example"></a>Przykład

Ten przykładowy kod generuje składnika za pomocą funkcji eksportowanych, natywnego, którego Konwencja wywołania jest niejawnie [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>Przykład

Poniższy przykład tworzy czystego klienta, który używa funkcji macierzystej. Jednak konwencji wywoływania, w obszarze **/CLR: pure** jest [__clrcall](../../cpp/clrcall.md). Poniższy przykład spowoduje wygenerowanie LNK2031.

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

Poniższy przykład pokazuje jak używać funkcji natywnej za pomocą czystego obrazu. Należy pamiętać, jawnie **__cdecl** wywoływania specyfikator Konwencji.

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```