---
title: '#using, dyrektywa (C++/CLI)'
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
ms.openlocfilehash: 0245eb15219585421be83def0258415ab4b573b6
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684264"
---
# <a name="using-directive-ccli"></a>#using — dyrektywa (C++/CLI)

Importuje metadane do programu skompilowanego z [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="syntax"></a>Składnia

> **`#using`***plik* [ **`as_friend`** ]

### <a name="parameters"></a>Parametry

*rozszerzeniem*\
Język pośredni (MSIL) firmy Microsoft *`.dll`* , *`.exe`* , *`.netmodule`* lub *`.obj`* plik. Przykład:

`#using <MyComponent.dll>`

**`as_friend`**\
Określa, że wszystkie typy w *pliku* są dostępne. Aby uzyskać więcej informacji, zobacz [zaprzyjaźnione zestawy (C++)](../dotnet/friend-assemblies-cpp.md).

## <a name="remarks"></a>Uwagi

*plik* może być plikiem języka pośredniego firmy Microsoft (MSIL), który można zaimportować do zarządzanych i zarządzanych konstrukcji. Jeśli biblioteka DLL zawiera manifest zestawu, zostaną zaimportowane wszystkie biblioteki DLL, do których odwołuje się manifest. Kompilowany zestaw będzie zawierać listę *plików* w metadanych jako odwołanie do zestawu.

Prawdopodobnie *plik* nie zawiera zestawu (*plik* jest moduł) i nie zamierzasz używać informacji o typie z modułu w bieżącej aplikacji (zestawu). Może wskazywać, że moduł jest częścią zestawu przy użyciu [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). Typy w module byłyby dostępne dla każdej aplikacji, która odwołuje się do zestawu.

Alternatywą do użycia **`#using`** jest opcja kompilatora [/Fu](../build/reference/fu-name-forced-hash-using-file.md) .

zestawy. exe przesłane do **`#using`** powinny być kompilowane przy użyciu jednego z kompilatorów programu .NET Visual Studio (na przykład Visual Basic lub Visual C#).  Próba zaimportowania metadanych z zestawu. exe skompilowanego za pomocą **`/clr`** spowoduje wyjątek ładowania pliku.

> [!NOTE]
> Składnik, do którego odwołuje się program, **`#using`** może być uruchamiany z inną wersją pliku zaimportowanego w czasie kompilacji, co sprawia, że aplikacja kliencka będzie dawać nieoczekiwane wyniki.

Aby kompilator rozpoznał typ w zestawie (a nie w module), należy go wymusić, aby rozpoznać typ. Można wymusić to na przykład przez zdefiniowanie wystąpienia typu. Istnieją inne sposoby rozwiązywania nazw typów w zestawie dla kompilatora. Na przykład, jeśli dziedziczysz z typu w zestawie, nazwa typu będzie znana kompilatorowi.

Podczas importowania metadanych utworzonych z kodu źródłowego, który został użyty [`__declspec(thread)`](../cpp/thread.md) , semantyka wątku nie jest utrwalana w metadanych. Na przykład zmienna zadeklarowana z **`__declspec(thread)`** , skompilowana w programie, który jest skompilowany dla .NET Framework środowiska uruchomieniowego języka wspólnego, a następnie zaimportowana przez **`#using`** , nie będzie miała **`__declspec(thread)`** semantyki dla zmiennej.

Wszystkie importowane typy (zarządzane i natywne) w pliku, do którego istnieje odwołanie **`#using`** , są dostępne, ale kompilator traktuje typy natywne jako deklaracje, a nie definicje.

mscorlib.dll jest automatycznie przywoływany podczas kompilowania przy użyciu **`/clr`** .

Zmienna środowiskowa LIBPATH określa katalogi do przeszukania, gdy kompilator rozpoznaje nazwy plików przesłane do **`#using`** .

Kompilator wyszukuje odwołania w następującej ścieżce:

- Ścieżka określona w **`#using`** instrukcji.

- Bieżący katalog.

- Katalog systemowy .NET Framework.

- Katalogi dodane z [`/AI`](../build/reference/ai-specify-metadata-directories.md) opcją kompilatora.

- Katalogi w zmiennej środowiskowej LIBPATH.

## <a name="examples"></a>Przykłady

Można skompilować zestaw, który odwołuje się do drugiego zestawu, który odwołuje się do trzeciego zestawu. Musisz tylko jawnie odwoływać się do trzeciego zestawu z pierwszego, jeśli jawnie używasz jednego z jego typów.

```cpp
// using_assembly_A.cpp
// compile with: /clr /LD
public ref class A {};
```

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

W poniższym przykładzie kompilator nie raportuje błędu dotyczącego odwoływania *using_assembly_A.dll*, ponieważ program nie używa żadnego z typów zdefiniowanych w *using_assembly_A. cpp*.

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
