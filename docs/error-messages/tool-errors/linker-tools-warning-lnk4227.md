---
title: Ostrzeżenie LNK4227 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4227
dev_langs:
- C++
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b56617ee355654dfbb198252ea37cdb344950cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4227"></a>Ostrzeżenie LNK4227 narzędzi konsolidatora  
  
> Ostrzeżenie operacji metadanych (*HRESULT*): *warning_message*  
  
Konsolidator Wykryto różnice metadanych podczas scalania:  
  
-   Jeden lub więcej zestawów występujących w odwołaniach w zestawie obecnie tworzony.  
  
-   Jeden lub więcej plików kodu źródłowego w kompilacji.  
  
Na przykład może być spowodowane LNK4227 Jeśli masz dwie funkcje globalne z tej samej nazwy, ale zadeklarowana w inny sposób informacji o parametrach (to znaczy deklaracje nie są spójne z wszystkie jednostki kompilacji). Ildasm.exe można użyć /METADATA *object_file* na każdym pliku obj, aby zobaczyć, jak typy są różne.  
  
LNK4227 służy również do raportów dotyczących problemów, które pochodzą z innego narzędzia. Wyszukaj komunikat ostrzegawczy, aby uzyskać więcej informacji.  
  
Problemy z metadanych musi mieć stałą rozwiązać ostrzeżenia.  
  
## <a name="example"></a>Przykład  
  
LNK4227 jest generowany, gdy inaczej niż zestaw, który odwołuje się on do podpisania przywoływanego zestawu.  
  
Poniższy przykład generuje LNK4227:  
  
```cpp  
// LNK4227.cpp  
// compile with: /clr  
using namespace System::Reflection;  
  
[assembly:AssemblyDelaySignAttribute(false)];  
  
int main() {}  
```  
  
 a następnie  
  
```cpp  
// LNK4227b.cpp  
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe  
using namespace System::Reflection;  
using namespace System::Runtime::CompilerServices;  
  
[assembly:AssemblyDelaySignAttribute(true)];  
// Try the following line instead  
// [assembly:AssemblyDelaySignAttribute(false)];  
  
ref class MyClass  
{  
};  
```  
  
## <a name="example"></a>Przykład  
  
LNK4227 również mogą być generowane, gdy numery wersji w niewłaściwym formacie są przekazywane do zestawu atrybutów.  "*" Jest specyficzne dla `AssemblyVersionAttribute`.  Aby usunąć to ostrzeżenie, użyj tylko numery w atrybutach wersji innych niż `AssemblyVersionAttribute`.  
  
Poniższy przykład generuje LNK4227:  
  
```cpp  
// LNK4227e.cpp  
// compile with: /clr /LD /W1  
using namespace System::Reflection;  
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK  
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227  
// try the following line instead  
// [assembly:AssemblyFileVersionAttribute("2.3")];  
```