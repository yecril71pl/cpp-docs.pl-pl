---
title: Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS
ms.date: 11/04/2016
f1_keywords:
- afx_ext_class
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
ms.openlocfilehash: 521fa0e0f786111e4e273685d2db6f6d011c72c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482579"
---
# <a name="exporting-and-importing-using-afxextclass"></a>Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS

[Biblioteki DLL rozszerzeń MFC](../build/extension-dlls-overview.md) użyć makra **AFX_EXT_CLASS** Aby wyeksportować klasy; pliki wykonywalne, które łączą się rozszerzenia MFC biblioteki DLL użyć makra, aby zaimportować klasy. Za pomocą **AFX_EXT_CLASS** — makro, ten sam pliki nagłówkowe, które są używane w celu skompilowania rozszerzenia MFC biblioteki DLL mogą być używane z pliki wykonywalne, które łącze do biblioteki DLL.

W pliku nagłówka dla biblioteki DLL, należy dodać **AFX_EXT_CLASS** — słowo kluczowe z deklaracją klasy, w następujący sposób:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

To makro jest definiowane przez MFC jako `__declspec(dllexport)` podczas symboli preprocesora `_AFXDLL` i `_AFXEXT` są zdefiniowane. Ale makro jest zdefiniowany jako `__declspec(dllimport)` podczas `_AFXDLL` jest zdefiniowana i `_AFXEXT` nie został zdefiniowany. Po zdefiniowaniu symbol preprocesora `_AFXDLL` wskazuje, że udostępnionej wersja MFC jest on używany przez element docelowy pliku wykonywalnego (biblioteki DLL lub aplikacji). Gdy oba `_AFXDLL` i `_AFXEXT` są zdefiniowane, oznacza to, czy docelowego pliku wykonywalnego jest rozszerzenia MFC biblioteki DLL.

Ponieważ `AFX_EXT_CLASS` jest zdefiniowany jako `__declspec(dllexport)` podczas eksportowania z biblioteki DLL rozszerzenia MFC, bez wprowadzania nazwy dekorowane wszystkie symbole tej klasy w pliku .def, można eksportować całej klasy.

Mimo że można uniknąć, tworząc plik .def i wszystkie nazwy dekorowane dla klasy przy użyciu tej metody, tworząc plik .def jest bardziej wydajne, ponieważ nazwy mogą być wyeksportowane według liczby porządkowej. Aby użyć metody plik .def eksportowania, umieść następujący kod na początku i na końcu pliku nagłówka:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
>  Należy zachować ostrożność, eksportowanie funkcji śródwierszowych, ponieważ tworzą konfliktów wersji. Funkcja śródwierszowa rozwija się w kodzie aplikacji; w związku z tym jeśli przepiszesz później funkcji, go nie zostanie zaktualizowany, chyba że sama aplikacja jest ponownie kompilowana. Zazwyczaj można zaktualizować funkcji DLL bez ponownie skompilować aplikacje, które z nich korzystają.

## <a name="exporting-individual-members-in-a-class"></a>Eksportowanie poszczególnych elementów członkowskich w klasie

Czasami możesz chcieć wyeksportować poszczególnych elementów członkowskich klasy. Na przykład jeśli eksportujesz `CDialog`-klasy pochodne mogą tylko należy wyeksportować konstruktora i `DoModal` wywołania. Możesz użyć `AFX_EXT_CLASS` na poszczególnych elementów członkowskich, należy wyeksportować.

Na przykład:

```cpp
class CExampleDialog : public CDialog
{
public:
   AFX_EXT_CLASS CExampleDialog();
   AFX_EXT_CLASS int DoModal();
   ...
   // rest of class definition
   ...
};
```

Ponieważ wszystkie elementy członkowskie klasy nie są eksportowane, mogą występować dodatkowe problem ze względu na sposób współpracujące makr MFC. Zadeklaruj kilka makra pomocnika MFC faktycznie lub zdefiniować elementy członkowskie danych. Dlatego te elementy członkowskie danych musi być eksportowany z biblioteki DLL.

Na przykład `DECLARE_DYNAMIC` podczas kompilowania biblioteki DLL rozszerzenia MFC — makro jest zdefiniowany następująco:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

Wiersz zaczynający się za pomocą statycznych `AFX_DATA` jest deklarowania obiektu statycznego wewnątrz klasy. Aby eksportować tej klasy prawidłowo i uzyskać dostęp do informacji czasu wykonywania w kliencie pliku wykonywalnego, możesz wyeksportować tego obiektu statycznego. Ponieważ obiektu statycznego jest zadeklarowana za pomocą modyfikatora `AFX_DATA`, musisz zdefiniować `AFX_DATA` jako `__declspec(dllexport)` podczas kompilowania biblioteki DLL i zdefiniuj go w formie `__declspec(dllimport)` podczas kompilowania pliku wykonywalnego klienta. Ponieważ `AFX_EXT_CLASS` jest już zdefiniowany w ten sposób, wystarczy ponownie zdefiniować `AFX_DATA` być taka sama jak `AFX_EXT_CLASS` wokół swojej definicji klasy.

Na przykład:

```cpp
#undef  AFX_DATA
#define AFX_DATA AFX_EXT_CLASS

class CExampleView : public CView
{
   DECLARE_DYNAMIC()
   // ... class definition ...
};

#undef  AFX_DATA
#define AFX_DATA
```

Ponieważ MFC zawsze używa `AFX_DATA` symboli dla elementów danych definiuje się on w makrach, ta technika działa, w przypadku takich scenariuszy. Na przykład działa w przypadku `DECLARE_MESSAGE_MAP`.

> [!NOTE]
>  Jeśli eksportujesz całej klasy, a nie wybrane elementy członkowskie klasy automatycznie eksportowane są statyczne elementy członkowskie danych.

### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL za pomocą plików .def](../build/exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportuj funkcje C++ do użycia w plikach wykonywalnych języka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Eksportuj funkcje C do użycia w plikach wykonywalnych języka C lub języka C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Określić, której metody eksportowania użyjesz](../build/determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Zainicjuj bibliotekę DLL](../build/run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Nazwy ozdobione](../build/reference/decorated-names.md)

- [Importowanie i eksportowanie funkcji śródwierszowych](../build/importing-and-exporting-inline-functions.md)

- [Importy wzajemne](../build/mutual-imports.md)

## <a name="see-also"></a>Zobacz też

[Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)