---
title: '#Dyrektywa using (C++/CLI)'
ms.date: 08/29/2019
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
ms.openlocfilehash: 5dae5c277055157aef5451c19ee020fbbd2aaccb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220200"
---
# <a name="using-directive-ccli"></a>#using — dyrektywaC++(/CLI)

Importuje metadane do programu skompilowanego z [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="syntax"></a>Składnia

> **#using** *plik* [**as_friend**]

### <a name="parameters"></a>Parametry

*rozszerzeniem*\
Plik MSIL. dll,. exe,. Na przykład

`#using <MyComponent.dll>`

**as_friend**\
Określa, że wszystkie typy w *pliku* są dostępne. Aby uzyskać więcej informacji, zobacz [zaprzyjaźnioneC++zestawy ()](../dotnet/friend-assemblies-cpp.md).

## <a name="remarks"></a>Uwagi

*plik* może być plikiem języka pośredniego firmy Microsoft (MSIL), który można zaimportować do zarządzanych i zarządzanych konstrukcji. Jeśli plik. dll zawiera manifest zestawu, wszystkie biblioteki DLL, do których odwołuje się manifest, są importowane, a kompilowany zestaw będzie listować *plik* w metadanych jako odwołanie do zestawu.

Jeśli *plik* nie zawiera zestawu (Jeśli *plik* jest moduł) i jeśli nie zamierzasz używać informacji o typie z modułu w bieżącej aplikacji (zestawu), masz możliwość wskazywania, że moduł jest częścią zestawu; Użyj [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). Typy w module byłyby dostępne dla każdej aplikacji, która odwołuje się do zestawu.

Alternatywą dla użycia **#using** jest opcja kompilatora [/Fu](../build/reference/fu-name-forced-hash-using-file.md) .

zestawy. exe przesłane do **#using** powinny być kompilowane przy użyciu jednego z kompilatorów programu .NET Visual Studio (na przykład Visual Basic C#lub wizualizacji).  Próba zaimportowania metadanych z zestawu. exe skompilowanego za `/clr` pomocą spowoduje wyjątek ładowania pliku.

> [!NOTE]
> Składnik, do którego odwołuje się **#using** , może być uruchamiany z inną wersją pliku zaimportowanego w czasie kompilacji, co sprawia, że aplikacja kliencka będzie dawać nieoczekiwane wyniki.

Aby kompilator rozpoznał typ w zestawie (a nie w module), należy go wymusić, aby rozpoznać typ. Można wymusić to na przykład przez zdefiniowanie wystąpienia typu. Istnieją inne sposoby rozwiązywania nazw typów w zestawie dla kompilatora. Na przykład, jeśli dziedziczysz z typu w zestawie, nazwa typu będzie znana kompilatorowi.

Podczas importowania metadanych utworzonych z kodu źródłowego, który używa [__declspec (thread)](../cpp/thread.md), semantyka wątku nie jest utrwalana w metadanych. Na przykład zmienna zadeklarowana przy użyciu **__declspec (thread)** , skompilowana w programie, który jest skompilowany dla .NET Framework środowiska uruchomieniowego języka wspólnego, a następnie zaimportowana za pośrednictwem **#using**, nie będzie miała semantyki **__declspec (thread)** dla zmiennej.

Dostępne są wszystkie typy importowane (zarządzane i natywne) w pliku, do którego odwołuje się **#using** , ale kompilator traktuje typy natywne jako deklaracje, a nie definicje.

plik mscorlib. dll jest automatycznie przywoływany `/clr`podczas kompilowania przy użyciu.

Zmienna środowiskowa LIBPATH określa katalogi do przeszukania, gdy kompilator rozpoznaje nazwy plików przesłane do **#using**.

Kompilator wyszukuje odwołania w następującej ścieżce:

- Ścieżka określona w instrukcji **#using** .

- Bieżący katalog.

- Katalog systemowy .NET Framework.

- Katalogi dodane z opcją kompilatora [/AI](../build/reference/ai-specify-metadata-directories.md) .

- Katalogi w zmiennej środowiskowej LIBPATH.

## <a name="example"></a>Przykład

Jeśli kompilujesz zestaw (C) i odwołujesz się do zestawu (B), który sam odwołuje się do innego zestawu (A), nie musisz jawnie odwoływać się do zestawu, chyba że jawnie używasz jednego z typów w C.

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

W poniższym przykładzie nie istnieje błąd kompilatora dla nieodwoływania się do *using_assembly_A. dll*, ponieważ program nie używa żadnego z typów zdefiniowanych w *using_assembly_A. cpp*.

```cpp
// using_assembly_C.cpp
// compile with: /clr
#using "using_assembly_B.dll"
int main() {
   B b;
   b.Test();
}
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)
