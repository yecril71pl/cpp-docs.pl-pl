---
title: "Platformy, domyślna i cli przestrzenie nazw (C++ Component Extensions) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- lang
- cli
dev_langs: C++
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bde9c1d76c2c8196f7773a8af042acb2ef0d2d89
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="platform-default-and-cli-namespaces--c-component-extensions"></a>Przestrzeń nazw platformy, domyślna i cli (C++ Component Extensions)
Przestrzeń nazw kwalifikuje nazwy elementów języka, tak aby nazwy nie były sprzeczne z identycznymi nazwami zdefiniowanymi w innych miejscach w kodzie źródłowym. Na przykład kolizję nazw może uniemożliwić kompilatorowi rozpoznawanie [słowa kluczowe Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md). Przestrzenie nazw są używane przez kompilator, ale nie są zachowywane w skompilowanym zestawie.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 Visual C++ zapewnia domyślną przestrzeń nazw dla projektu podczas tworzenia projektu. Można ręcznie zmień nazwę przestrzeni nazw, mimo że środowisko wykonawcze systemu Windows nazwa pliku winmd musi odpowiadać nazwie głównej przestrzeni nazw.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Aby uzyskać więcej informacji, zobacz [obszary nazw i typ widoczności (C + +/ CX)](http://msdn.microsoft.com/library/windows/apps/hh969551.aspx).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 **Składnia**  
  
```  
using namespace cli;  
```  
  
 **Uwagi**  
  
 C + +/ CLI obsługuje `cli` przestrzeni nazw. Podczas kompilowania za pomocą **/CLR**, `using` technicznego instrukcji w sekcji składni.  
  
 Następujące funkcje językowe znajdują się w `cli` przestrzeni nazw:  
  
-   [Tablice](../windows/arrays-cpp-component-extensions.md)  
  
-   [interior_ptr (C + +/ CLI)](../windows/interior-ptr-cpp-cli.md)  
  
-   [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md)  
  
-   [safe_cast](../windows/safe-cast-cpp-component-extensions.md)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Poniższy przykład kodu pokazuje, czy jest możliwe użycie symbolu w `cli` przestrzeń nazw jako symbol w kodzie użytkownika.  Jednak po zostało to zrobione, należy jawnie lub niejawnie z odwołań do kwalifikowania `cli` języka element o takiej samej nazwie.  
  
```  
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