---
title: Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- afx_ext_class
dev_langs:
- C++
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6cc853c66afae72d6e426d800c0443ab206ab20
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371063"
---
# <a name="exporting-and-importing-using-afxextclass"></a>Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS  
  
[Biblioteki DLL rozszerzeń MFC](../build/extension-dlls-overview.md) użyć makra **afx_ext_class —** Aby wyeksportować klasy, plików wykonywalnych, które łącze do biblioteki DLL rozszerzenia MFC przy użyciu makra można zaimportować klas. Z **afx_ext_class —** makra, tych samych plików nagłówka, które są używane do tworzenia rozszerzenia MFC DLL może być używany z plików wykonywalnych, które łącze do pliku DLL.  
  
 W pliku nagłówka dla biblioteki DLL, Dodaj **afx_ext_class —** — słowo kluczowe do deklaracji klasy w następujący sposób:  
  
```cpp  
class AFX_EXT_CLASS CMyClass : public CDocument  
{  
// <body of class>  
};  
```  
  
To makro jest definiowana za pomocą MFC jako `__declspec(dllexport)` podczas symboli preprocesora `_AFXDLL` i `_AFXEXT` są zdefiniowane. Ale makro jest zdefiniowany jako `__declspec(dllimport)` podczas `_AFXDLL` zdefiniowano i `_AFXEXT` nie jest zdefiniowany. Po zdefiniowaniu symbol preprocesora `_AFXDLL` wskazuje, czy wersja udostępnionego MFC jest używany przez docelowego pliku wykonywalnego (biblioteki DLL lub aplikacji). Gdy zarówno `_AFXDLL` i `_AFXEXT` są zdefiniowane, to oznacza, że element docelowy pliku wykonywalnego jest bibliotekę DLL rozszerzenia MFC.  
  
Ponieważ `AFX_EXT_CLASS` jest zdefiniowany jako `__declspec(dllexport)` podczas eksportowania z biblioteki DLL rozszerzenia MFC, można wyeksportować całą klasy bez wprowadzania nazwy ozdobione wszystkie symbole tej klasy w pliku .def.  
  
Mimo że można uniknąć, tworzenia plik .def i wszystkie nazwy ozdobione dla klasy z tą metodą, tworząc plik .def jest bardziej wydajne, ponieważ nazwy mogą być eksportowane według liczby porządkowej. Przy użyciu metody plik .def eksportowania, należy umieścić na początku i na końcu pliku nagłówka następujący kod:  
  
```cpp  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
> [!CAUTION]
>  Należy zachować ostrożność, gdy eksportowanie funkcji śródwierszowych, ponieważ mogą one tworzyć konfliktów wersji. Funkcja wbudowana pobiera rozwinięty w kodzie aplikacji; w związku z tym jeśli później ponownego zapisywania funkcji go nie zostanie zaktualizowany, chyba że sama aplikacja jest ponownie kompilowana. Zwykle funkcje DLL może zostać zaktualizowana bez odbudowywania aplikacje, które z nich korzystają.  
  
## <a name="exporting-individual-members-in-a-class"></a>Eksportowanie poszczególnych elementów członkowskich w klasie  
  
Czasami można wyeksportować poszczególnych członków klasy. Na przykład w przypadku eksportowania `CDialog`-klasy, może być tylko należy wyeksportować konstruktora i `DoModal` wywołania. Można użyć `AFX_EXT_CLASS` na poszczególnych członków, należy wyeksportować.  
  
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
  
Ponieważ wszystkie elementy członkowskie klasy nie są eksportowane, może wystąpić problem dodatkowe ze względu na sposób pracy makr MFC. Kilka makra pomocnika MFC faktycznie zadeklarować lub Zdefiniuj elementy członkowskie danych. W związku z tym te elementy członkowskie danych również należy wyeksportować z biblioteki DLL.  
  
Na przykład `DECLARE_DYNAMIC` podczas tworzenia biblioteki DLL rozszerzenia MFC — makro jest zdefiniowane w następujący sposób:  
  
```cpp  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
   static CRuntimeClass* PASCAL _GetBaseClass(); \  
public: \  
   static AFX_DATA CRuntimeClass class##class_name; \  
   virtual CRuntimeClass* GetRuntimeClass() const; \  
```  
  
Wiersz rozpoczynający się od statycznej `AFX_DATA` jest deklarowanie obiektu statycznego wewnątrz klasy. Aby wyeksportować ta klasa poprawnie i uzyskać dostęp do informacji czasu wykonywania w kliencie pliku wykonywalnego, możesz wyeksportować tego obiektu statycznego. Ponieważ obiektu statycznego jest zadeklarowana z modyfikatorem `AFX_DATA`, musisz zdefiniować `AFX_DATA` jako `__declspec(dllexport)` podczas tworzenia biblioteki DLL i zdefiniować ją jako `__declspec(dllimport)` podczas kompilowania pliku wykonywalnego klienta. Ponieważ `AFX_EXT_CLASS` jest już zdefiniowany w ten sposób, wystarczy ponownie zdefiniować `AFX_DATA` być taka sama jak `AFX_EXT_CLASS` wokół definicję klasy.  
  
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
  
Ponieważ MFC zawsze używa `AFX_DATA` symbolu elementów danych definiuje w makrach, ta technika działa w przypadku wszystkich takich scenariuszy. Na przykład działa `DECLARE_MESSAGE_MAP`.  
  
> [!NOTE]
>  Eksportowania całej klasy, a nie zaznaczone elementy członkowskie klasy statyczne elementy członkowskie danych automatycznie są eksportowane.  
  
### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Eksportowanie z biblioteki DLL przy użyciu .def — pliki](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Eksportowanie funkcji języka C do użycia w plikach wykonywalnych języka C lub języka C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Określić jakiej metody eksportu użyć](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicjowanie biblioteki DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Nazwy ozdobione](../build/reference/decorated-names.md)  
  
-   [Importowanie i eksportowanie funkcji śródwierszowych](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importy wzajemne](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)