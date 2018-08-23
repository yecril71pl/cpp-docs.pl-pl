---
title: Platformy, domyślna i cli przestrzenie nazw (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- lang
- cli
dev_langs:
- C++
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cde444e807aa6fe2276b4bfe9b0b9c4bc0476103
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610557"
---
# <a name="platform-default-and-cli-namespaces--c-component-extensions"></a>Przestrzeń nazw platformy, domyślna i cli (C++ Component Extensions)

Przestrzeń nazw kwalifikuje nazwy elementów języka, tak aby nazwy nie były sprzeczne z identycznymi nazwami zdefiniowanymi w innych miejscach w kodzie źródłowym. Na przykład kolizja nazwy może uniemożliwić kompilatorowi rozpoznawaniu [Context-Sensitive Keywords](../windows/context-sensitive-keywords-cpp-component-extensions.md). Przestrzenie nazw są używane przez kompilator, ale nie są zachowywane w skompilowanym zestawie.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

Visual C++ zapewnia domyślną przestrzeń nazw dla projektu podczas tworzenia projektu. Można ręcznie zmień nazwę przestrzeni nazw, mimo że środowiska wykonawczego Windows, nazwa pliku winmd musi odpowiadać nazwie głównej przestrzeni nazw.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Aby uzyskać więcej informacji, zobacz [przestrzenie nazw i typ widoczności (C + +/ CX)](http://msdn.microsoft.com/library/windows/apps/hh969551.aspx).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="syntax"></a>Składnia

```cpp
using namespace cli;
```

### <a name="remarks"></a>Uwagi

C + +/ interfejsu wiersza polecenia obsługuje **interfejsu wiersza polecenia** przestrzeni nazw. Podczas kompilowania za pomocą `/clr`, **przy użyciu** jest implikowane instrukcji w sekcji składni.

Następujące funkcje języka znajdują się w **interfejsu wiersza polecenia** przestrzeni nazw:

- [Tablice](../windows/arrays-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)

- [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)

- [przedstawienie operacji safe_cast](../windows/safe-cast-cpp-component-extensions.md)

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład kodu demonstruje, że istnieje możliwość używania symbolu w **interfejsu wiersza polecenia** przestrzeni nazw jako symbol w kodzie użytkownika.  Jednak po zostało to zrobione, będzie konieczne jawne lub niejawne określenie odwołań do **interfejsu wiersza polecenia** element języka o takiej samej nazwie.

```cpp
// cli_namespace.cpp
// compile with: /clr
using namespace cli;
int main() {
   array<int> ^ MyArray = gcnew array<int>(100);
   int array = 0;

   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062

   // OK
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);
}
```

## <a name="see-also"></a>Zobacz też

[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)