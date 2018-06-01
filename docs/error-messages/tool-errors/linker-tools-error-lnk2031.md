---
title: Błąd narzędzi konsolidatora LNK2031 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2031
dev_langs:
- C++
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d86ea6da8a73d9ba2427e9455c4fca87cd32dd2b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703668"
---
# <a name="linker-tools-error-lnk2031"></a>Błąd narzędzi konsolidatora LNK2031

> Nie można wygenerować p/invoke dla elementu "*function_declaration*" *decorated_name*; Brak konwencji wywoływania w metadanych

## <a name="remarks"></a>Uwagi

Podczas próby importowanie funkcji macierzystej czysty obraz, należy pamiętać, że niejawne konwencji wywoływania różnią się w kompilacjach kodu natywnego i czysty. Aby uzyskać więcej informacji o obrazach czystego, zobacz [czystej i weryfikowalny kod (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

**/CLR: pure** — opcja kompilatora jest przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

## <a name="example"></a>Przykład

Ten przykładowy kod generuje składnika z funkcją wyeksportowany, natywnego, których Konwencja wywoływania jest niejawnie [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>Przykład

W poniższym przykładzie tworzone czysty klienta, który używa funkcji macierzystej. Jednak Konwencja wywoływania w obszarze **/CLR: pure** jest [__clrcall](../../cpp/clrcall.md). Poniższy przykład generuje LNK2031.

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

Poniższy przykład przedstawia sposób korzystać z funkcji macierzystej czysty obraz. Należy zwrócić uwagę jawnych **__cdecl** specyfikator konwencji wywoływania.

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```