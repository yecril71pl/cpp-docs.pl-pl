---
title: '#Using — Dyrektywa (C + +/ CLR) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
dev_langs:
- C++
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 053c425a6bb8dcab0dc5cb94db1537f0fff3d9f8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33840739"
---
# <a name="using-directive-cclr"></a>#using — dyrektywa (C + +/ CLR)
Importuje metadane do programu skompilowane z [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
#using file [as_friend]  
```  
  
#### <a name="parameters"></a>Parametry  
 `file`  
 DLL MSIL, .exe, modułu .netmodule, lub. obiektu Na przykład  
  
 `#using <MyComponent.dll>`  
  
 as_friend  
 Określa, że wszystkie typy w `file` są dostępne.  Aby uzyskać więcej informacji, zobacz [przyjazne zestawy (C++)](../dotnet/friend-assemblies-cpp.md).  
  
## <a name="remarks"></a>Uwagi  
 `file` może być importowany plik języka pośredniego (MSIL) firmy Microsoft danych zarządzanych i zarządzanych konstrukcji. Jeśli plik dll zawiera manifest zestawu, a następnie są importowane wszystkie biblioteki, do której odwołuje się do manifestu i wyświetla zestaw jest konstruowany *pliku* w metadanych jako odwołanie do zestawu.  
  
 Jeśli `file` nie zawiera zestawu (Jeśli `file` jest modułem) i jeśli nie zamierzasz użyć informacji o typie z modułu w bieżącej aplikacji (assembly), masz możliwość tylko wskazującą, czy moduł jest częścią zestawu; użyj [/Assemblymodule](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). Typy w module będzie wówczas dostępne dla dowolnej aplikacji, która odwołuje się do zestawu.  
  
 Zamiast używać `#using` jest [/FU](../build/reference/fu-name-forced-hash-using-file.md) — opcja kompilatora.  
  
 zestawy .exe przekazany do `#using` ma być kompilowana przy użyciu jednej z kompilatorów programu Visual Studio .NET (Visual Basic lub Visual C#, na przykład).  Podjęto próbę Importowanie metadanych z zestawu .exe skompilowanego z **/CLR** spowodują wyjątek ładowania pliku.  
  
> [!NOTE]
>  Składnik, do którego odwołuje się z `#using` mogą być uruchamiane w innej wersji pliku zaimportowany w czasie kompilacji, powodując aplikacji klienckiej dać nieoczekiwane wyniki.  
  
 Kompilator, aby rozpoznać typu w zestawie (nie w module), konieczne można wymusić można rozpoznać typu, co można zrobić, na przykład, definiując wystąpienia typu. Istnieją inne sposoby rozwiązania nazwy typów w zestawie dla kompilatora, na przykład, jeśli dziedziczyć z typu w zestawie, nazwa typu zostanie następnie stają się wiadomo kompilatora.  
  
 Podczas importowania metadanych skompilowane z kodu źródłowego, który używany [__declspec(thread)](../cpp/thread.md), semantyki wątku nie są zachowywane w metadanych. Na przykład Zmienna zadeklarowana ze **__declspec(thread)** skompilowanych w programie kompilacji dla platformy .NET Framework środowisko uruchomieniowe języka wspólnego, a następnie importować za pomocą `#using`, nie będą już dostępne **__declspec () Wątek)** semantyki zmiennej.  
  
 Zaimportować wszystkie typy (zarządzane i natywne) w pliku odwołuje się `#using` są dostępne, ale kompilator natywnych typów traktuje jako deklaracje nie definicje.  
  
 mscorlib.dll odwołuje się automatycznie podczas kompilowania za pomocą **/CLR**.  
  
 Libpath-zmienna środowiskowa Określa katalogi, które będą przeszukiwane, gdy kompilator próbuje rozpoznać nazwy plików przekazanych do `#using`.  
  
 Kompilator umożliwia wyszukiwanie odwołań w następującej ścieżce:  
  
-   Ścieżka określona w `#using` instrukcji.  
  
-   Bieżący katalog.  
  
-   Katalog systemu .NET Framework.  
  
-   Katalogi dodane z [/AI](../build/reference/ai-specify-metadata-directories.md) — opcja kompilatora.  
  
-   Katalogi w zmiennej środowiskowej LIBPATH.  
  
## <a name="example"></a>Przykład  
 Jeśli kompilacji zestawu (C) i odwołanie do zestawu (B) czy się odwołuje się do innego zestawu (A), nie musisz jawnie odwoływać A zestawu, chyba że jawnie za pomocą jednego z jego A typów w C.  
  
```  
// using_assembly_A.cpp  
// compile with: /clr /LD  
public ref class A {};  
```  
  
## <a name="example"></a>Przykład  
  
```  
// using_assembly_B.cpp  
// compile with: /clr /LD  
#using "using_assembly_A.dll"  
public ref class B {  
public:  
   void Test(A a) {}  
   void Test() {}  
};  
  
```  
  
## <a name="example"></a>Przykład  
 W następującym przykładowym nie ma żadnych nie odwołuje się do using_assembly_A.dll, ponieważ program nie używa żadnego z typów definiowanych w using_assembly_A.cpp błąd kompilatora.  
  
```  
// using_assembly_C.cpp  
// compile with: /clr  
#using "using_assembly_B.dll"  
int main() {  
   B b;  
   b.Test();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)