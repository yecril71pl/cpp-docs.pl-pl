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
ms.openlocfilehash: 95c72f8251a8a59833483eb948709c80a69d03d7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328610"
---
# <a name="exporting-and-importing-using-afx_ext_class"></a>Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS

[Biblioteki DLL rozszerzenia MFC](extension-dlls-overview.md) używają **AFX_EXT_CLASS** makr do eksportowania klas; pliki wykonywalne, które łączą się z biblioteką DLL rozszerzenia MFC, używają makra do importowania klas. W przypadku makra **AFX_EXT_CLASS** te same pliki nagłówkowe, które są używane do tworzenia biblioteki DLL rozszerzenia MFC, mogą być używane z plikami wykonywalnymi łączącymi się z biblioteką DLL.

W pliku nagłówka biblioteki DLL dodaj słowo kluczowe **AFX_EXT_CLASS** do deklaracji klasy w następujący sposób:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

To makro jest definiowane `__declspec(dllexport)` przez MFC, jak `_AFXDLL` wtedy, gdy symbole preprocesora i `_AFXEXT` są zdefiniowane. Ale makro jest `__declspec(dllimport)` zdefiniowane jako gdy `_AFXDLL` jest zdefiniowane i `_AFXEXT` nie jest zdefiniowane. Po zdefiniowaniu symbol `_AFXDLL` preprocesora wskazuje, że udostępniona wersja MFC jest używana przez docelowy plik wykonywalny (biblioteka DLL lub aplikacja). Gdy `_AFXDLL` oba `_AFXEXT` i są zdefiniowane, oznacza to, że docelowy plik wykonywalny jest DLL rozszerzenia MFC.

Ponieważ `AFX_EXT_CLASS` jest `__declspec(dllexport)` zdefiniowany jako podczas eksportowania z biblioteki DLL rozszerzenia MFC, można wyeksportować całe klasy bez umieszczania dekoracyjne nazwy dla wszystkich symboli tej klasy w pliku .def.

Chociaż można uniknąć tworzenia pliku def i wszystkich dekoracyjnych nazw klasy za pomocą tej metody, tworzenie pliku def jest bardziej wydajne, ponieważ nazwy mogą być eksportowane przez porządkowe. Aby użyć metody eksportowania pliku def, umieść następujący kod na początku i na końcu pliku nagłówka:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
> Należy zachować ostrożność podczas eksportowania funkcji wbudowanych, ponieważ mogą one tworzyć możliwość konfliktów wersji. Funkcja wbudowana zostanie rozwinięta do kodu aplikacji; w związku z tym jeśli później przepisać funkcję, nie zostanie zaktualizowany, chyba że sama aplikacja jest ponownie skompilowany. Zwykle funkcje biblioteki DLL można aktualizować bez przebudowy aplikacji, które z nich korzystają.

## <a name="exporting-individual-members-in-a-class"></a>Eksportowanie poszczególnych członków w klasie

Czasami możesz chcieć wyeksportować poszczególnych członków swojej klasy. Na przykład w przypadku eksportowania klasy pochodnej, `CDialog`może być konieczne tylko `DoModal` wyeksportowanie konstruktora i wywołania. Możesz użyć `AFX_EXT_CLASS` na poszczególnych członków, które należy wyeksportować.

Przykład:

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

Ponieważ nie są już eksportowania wszystkich członków klasy, może napotkać dodatkowy problem ze względu na sposób, w jaki działają makra MFC. Kilka makr pomocnika MFC faktycznie deklaruje lub definiuje elementy członkowskie danych. W związku z tym te elementy członkowskie danych muszą być również eksportowane z biblioteki DLL.

Na przykład `DECLARE_DYNAMIC` makro jest zdefiniowane w następujący sposób podczas tworzenia biblioteki DLL rozszerzenia MFC:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

Wiersz, który zaczyna `AFX_DATA` się od statyczne jest deklarowanie obiektu statycznego wewnątrz klasy. Aby poprawnie wyeksportować tę klasę i uzyskać dostęp do informacji o czasie wykonywania z pliku wykonywalnego klienta, należy wyeksportować ten obiekt statyczny. Ponieważ obiekt statyczny jest zadeklarowany `AFX_DATA`za pomocą modyfikatora, wystarczy zdefiniować `AFX_DATA` podczas `__declspec(dllimport)` `__declspec(dllexport)` tworzenia biblioteki DLL i zdefiniować ją tak, jak podczas tworzenia pliku wykonywalnego klienta. Ponieważ `AFX_EXT_CLASS` jest już zdefiniowany w ten sposób, wystarczy przedefiniować, `AFX_DATA` aby być takie same, jak `AFX_EXT_CLASS` wokół definicji klasy.

Przykład:

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

Ponieważ MFC zawsze `AFX_DATA` używa symbolu na elementach danych, które definiuje w swoich makrach, ta technika działa dla wszystkich takich scenariuszy. Na przykład działa `DECLARE_MESSAGE_MAP`dla .

> [!NOTE]
> Jeśli eksportujesz całą klasę, a nie wybranych członków klasy, elementy członkowskie danych statycznych są eksportowane automatycznie.

### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL przy użyciu plików def](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie funkcji języka C++ do użytku w plikach wykonywalnych w języku C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Eksportowanie funkcji C do użytku w plikach wykonywalnych języka C lub C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Określanie, która metoda eksportowania ma być używana](determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicjowanie biblioteki DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>O czym chcesz wiedzieć więcej?

- [Nazwy zdobione](reference/decorated-names.md)

- [Importowanie i eksportowanie funkcji śródwierszowych](importing-and-exporting-inline-functions.md)

- [Wzajemny przywóz](mutual-imports.md)

## <a name="see-also"></a>Zobacz też

[Eksportowanie z biblioteki DLL](exporting-from-a-dll.md)
