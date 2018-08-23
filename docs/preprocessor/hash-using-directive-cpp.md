---
title: '#Using — Dyrektywa (C + +/ CLI) | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 8a43946100146def9c0082f533c3657d7ab8ebac
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465332"
---
# <a name="using-directive-ccli"></a>#using — dyrektywa (C + +/ CLI)
Importuje metadane do programu, który został skompilowany przy użyciu [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
#using file [as_friend]  
```  
  
### <a name="parameters"></a>Parametry  
*Plik*  
MSIL .dll, .exe, .netmodule, lub. obiektu Na przykład  
  
`#using <MyComponent.dll>`  
  
*as_friend*  
Określa, że wszystkie typy w *pliku* są dostępne. Aby uzyskać więcej informacji, zobacz [przyjazne zestawy (C++)](../dotnet/friend-assemblies-cpp.md).  
  
## <a name="remarks"></a>Uwagi  
 
*plik* może być importowanego pliku języka intermediate language (MSIL) firmy Microsoft dla swoich danych zarządzanych i zarządzanych konstrukcji. Jeśli pliku dll zawiera manifest zestawu, a następnie zostaną zaimportowane wszystkie biblioteki, do którego odwołuje się do manifestu zestawu, którą tworzysz, zostanie wyświetlona lista *pliku* w metadanych jako odwołanie do zestawu.  
  
Jeśli *pliku* nie zawiera zestawu (Jeśli *pliku* to moduł) i jeśli nie zamierzasz używać informacji o typie w module w bieżącej aplikacji (assembly), masz możliwość tylko wskazuje, że Moduł jest częścią zestawu; Użyj [assemblymodule](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). Typy w module będzie wówczas dostępne dla innych aplikacji, do którego odwołuje się zestaw.  
  
Alternatywa dla użycia **#using** jest [/FU](../build/reference/fu-name-forced-hash-using-file.md) — opcja kompilatora.  
  
zestawy .exe przekazany do **#using** powinna być skompilowana przy użyciu jednej z kompilatory programu Visual Studio .NET (Visual Basic lub Visual C#, na przykład).  Próby zaimportowania metadanych z zestawu .exe skompilowany przy użyciu `/clr` spowodują wyjątek ładowania pliku.  
  
> [!NOTE]
> Składnik, który jest wskazywane poprzez **#using** mogą być uruchamiane w innej wersji pliku zaimportowane w czasie kompilacji, co aplikacja kliencka dać nieoczekiwane wyniki.  
  
Kompilator rozpoznaje typu w zestawie (nie moduł), potrzebny zmuszeni do rozpoznania typu, co można zrobić, na przykład, określając wystąpienie tego typu. Istnieją inne sposoby rozwiązania nazwy typów w zestawie dla kompilatora, na przykład, jeśli dziedziczyć z typu w zestawie, nazwa typu następnie będzie stają się znane do kompilatora.  
  
Podczas importowania metadanych utworzona na podstawie kodu źródłowego, który używany [__declspec(thread)](../cpp/thread.md), semantyka wątku nie zostaną utrwalone w metadanych. Na przykład, Zmienna zadeklarowana ze **__declspec(thread)** skompilowanych w programie, to kompilacja dla .NET Framework środowisko uruchomieniowe języka wspólnego, a następnie importować za pomocą **#using**, nie będą już zawierały **__declspec(thread)** semantyki na zmiennej.  
  
Zaimportowane wszystkie typy (zarządzany i natywny) w pliku, który odwołuje się **#using** są dostępne, ale kompilator traktuje natywnych typów jako deklaracje nie definicje.  
  
Aby biblioteka mscorlib.dll odwołuje się automatycznie podczas kompilowania za pomocą `/clr`.  
  
Libpath-zmienna środowiskowa Określa katalogi, które będą przeszukiwane, gdy kompilator próbuje rozpoznać nazw plików przekazywane do **#using**.  
  
Kompilator będzie wyszukiwał odwołania w następującej ścieżce:  
  
- Ścieżka określona w **#using** instrukcji.  
  
- Bieżący katalog.  
  
- Katalog systemu .NET Framework.  
  
- Katalogi dodane za pomocą [/AI](../build/reference/ai-specify-metadata-directories.md) — opcja kompilatora.  
  
- Katalogi w zmiennej środowiskowej LIBPATH.  
  
## <a name="example"></a>Przykład  
 
Jeśli kompilacja zestawów (C), a następnie Odwołaj się do zestawu (B), że sam odwołuje się do innego zestawu (A), nie będziesz mieć jawnie odwołać zestawu A, chyba że jawnie za pomocą jednego z A typy w C.  
  
```cpp  
// using_assembly_A.cpp  
// compile with: /clr /LD  
public ref class A {};  
```  
  
## <a name="example"></a>Przykład  
  
```cpp  
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
 
W poniższym przykładzie nie ma błędu kompilatora dla niewskazującym using_assembly_A.dll, ponieważ program nie używa żadnego z typów zdefiniowanych w using_assembly_A.cpp.  
  
```cpp  
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