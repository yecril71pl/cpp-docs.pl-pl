---
title: com::ptr — Klasa
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::com::ptr::ptr
- msclr::com::ptr::Attach
- msclr::com::ptr::CreateInstance
- msclr::com::ptr::Detach
- msclr::com::ptr::GetInterface
- msclr::com::ptr::QueryInterface
- msclr::com::ptr::Release
- msclr::com::ptr::operator=
- msclr::com::ptr::operator->
- msclr::com::ptr::operator!
helpviewer_keywords:
- msclr::ptr class
ms.assetid: 0144d0e4-919c-45f9-a3f8-fbc9edba32bf
ms.openlocfilehash: 342c222b837e179e2e13dbbd27c88efc18b12332
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58774175"
---
# <a name="comptr-class"></a>com::ptr — Klasa

Otoka dla obiektu COM, który może służyć jako członek klasy CLR.  Otoka także automatyzuje zarządzanie okresem istnienia obiektu COM, zwalniając wszystkie należące do firmy odwołania do obiektu, gdy jego destruktor jest wywoływany. Odpowiednikiem [klasa CComPtr](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Składnia

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>Parametry

*_interface_type*<br/>
Interfejs COM.

## <a name="remarks"></a>Uwagi

Element `com::ptr` można również jako funkcja lokalna zmienna Aby uprościć różne zadania COM i automatyzować zarządzanie okresem istnienia.

A `com::ptr` nie można używać bezpośrednio jako parametru funkcji; Użyj [operator odwołania śledzenia](../extensions/tracking-reference-operator-cpp-component-extensions.md) lub [operator uchwytu do obiektu (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) zamiast tego.

Element `com::ptr` nie może być bezpośrednio zwracana przez funkcję; zamiast tego użyj dojście.

## <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu.  Wywoływanie metody publiczne klas wyników w wywołaniach do zamkniętego `IXMLDOMDocument` obiektu.  Próbka tworzy wystąpienie dokumentu XML, wypełnia niektóre prostego formatu XML i jest uproszczone przeszukiwania węzłów w drzewie przeanalizowany do drukowania pliku XML do konsoli.

```cpp
// comptr.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   void LoadXml(String^ xml) {
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);
      BSTR bstr = NULL;

      try {
         // load some XML into the document
         bstr = ::SysAllocString(pinnedXml);
         if (NULL == bstr) {
            throw gcnew OutOfMemoryException;
         }
         VARIANT_BOOL bIsSuccessful = false;
         // use operator -> to call IXMODOMDocument member function
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   // simplified function to write just the first xml node to the console
   void WriteXml() {
      IXMLDOMNode* pNode = NULL;

      try {
         // the first child of the document is the first real xml node
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            WriteNode(pNode);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   // simplified function that only writes the node
   void WriteNode(IXMLDOMNode* pNode) {
      BSTR bstr = NULL;

      try {
         // write out the name and text properties
         Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
         String^ strName = gcnew String(bstr);
         Console::Write("<{0}>", strName);
         ::SysFreeString(bstr);
         bstr = NULL;

         Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
         Console::Write(gcnew String(bstr));
         ::SysFreeString(bstr);
         bstr = NULL;

         Console::WriteLine("</{0}>", strName);
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // stream some xml into the document
      doc.LoadXml("<word>persnickety</word>");

      // write the document to the console
      doc.WriteXml();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
<word>persnickety</word>
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis| 
|---------|-----------| 
|[ptr::ptr](#ptr)|Konstruuje `com::ptr` opakowywać obiektu COM.| 
|[ptr::~ptr](#tilde-ptr)|Destructs `com::ptr`.| 

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|---------|-----------| 
|[ptr::Attach](#attach)|Dołącza do obiektów COM `com::ptr`.| 
|[ptr::CreateInstance](#createInstance)|Tworzy wystąpienie obiektu COM w ramach `com::ptr`.| 
|[ptr::Detach](#detach)|Rezygnuje własności obiektu COM, zwraca wskaźnik do obiektu.| 
|[ptr::GetInterface](#getInterface)|Tworzy wystąpienie obiektu COM w ramach `com::ptr`.| 
|[ptr::QueryInterface](#queryInterface)|Wykonuje kwerendę należących do obiektu COM dla interfejsu i dołącza wynik do innego `com::ptr`.| 
|[ptr::Release](#release)|Zwalnia wszystkie należące do firmy odwołania do obiektu COM.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|---------|-----------| 
|[PTR::operator, wartość —&gt;](#operator-arrow)|Operator dostępu do elementu członkowskiego, używany do wywoływania metod na należących do obiektu COM.| 
|[ptr::operator=](#operator-assign)|Dołącza do obiektów COM `com::ptr`.| 
|[PTR::operator, wartość&nbsp;bool](#operator-bool)|Operator przy użyciu `com::ptr` w wyrażeniu warunkowym.| 
|[ptr::operator!](#operator-logical-not)|Operator, aby określić, czy należących do obiektu COM jest nieprawidłowy.| 

## <a name="requirements"></a>Wymagania

**Plik nagłówkowy** \<msclr\com\ptr.h >

**Namespace** msclr::com

 

## <a name="ptr"></a>PTR::PTR

Zwraca wskaźnik do posiadanego obiektu COM.

```cpp
ptr();
ptr(
   _interface_type * p
);
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik interfejsu COM.

### <a name="remarks"></a>Uwagi

Przypisuje konstruktora bez argumentów `nullptr` do podstawowego dojścia obiektu. Przyszłe wywołania `com::ptr` będzie zweryfikować obiekt wewnętrzny i dyskretnie się niepowodzeniem, dopóki obiekt zostanie utworzony lub dołączone.

Konstruktor one-argument — dodaje odwołanie do obiektu COM, ale nie Zwolnij odwołanie do obiektu wywołującego, dzięki czemu obiekt wywołujący musi wywoływać `Release` obiektu COM naprawdę oddawać kontroli. Gdy `com::ptr`jego destruktor jest wywoływany automatycznie zwolni jego odwołania do obiektu COM.

Przekazywanie `NULL` do tego konstruktora jest taka sama jak wersja bez argumentów podczas wywoływania.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu. Pokazuje użycie obie wersje konstruktora.

```cpp
// comptr_ptr.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="tilde-ptr"></a>PTR:: ~ ptr

Destructs `com::ptr`.

```cpp
~ptr();
```

### <a name="remarks"></a>Uwagi

W chwili zniszczenia `com::ptr` zwalnia wszystkie odwołania jest właścicielem do jego obiektu COM. Przy założeniu, że istnieją żadnych innych odwołań do obiektów COM, będzie można usunąć obiektu COM i jego pamięć zwolniona.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu.  W `main` funkcji, dwa `XmlDocument` destruktory obiektów zostanie wywołana, gdy wykraczają poza zakres `try` bloku, wynikiem bazowego `com::ptr` destruktora, wywołana, zwalnianie wszystkich należących do odwołania do modelu COM obiekt.

```cpp
// comptr_dtor.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="attach"></a>PTR::attach

Dołącza do obiektów COM `com::ptr`.

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parametry

*_right*<br/>
Wskaźnik interfejsu COM do dołączenia.

### <a name="exceptions"></a>Wyjątki

Jeśli `com::ptr` już posiada odwołanie do obiektu COM `Attach` zgłasza <xref:System.InvalidOperationException>.

### <a name="remarks"></a>Uwagi

Wywołanie `Attach` odwołuje się do obiektu COM, ale nie zwalnia wywołującego odwołania do niego.

Przekazywanie `NULL` do `Attach` skutkuje bez działań.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu. `ReplaceDocument` Wywołania pierwszej funkcji elementu członkowskiego `Release` na dowolnym wcześniej należały do obiektu, a następnie wywołania `Attach` można dołączyć nowy obiekt dokumentu.

```cpp
// comptr_attach.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc.Attach(pDoc);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by our ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="createInstance"></a>PTR::CreateInstance

Tworzy wystąpienie obiektu COM w ramach `com::ptr`.

```cpp
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   System::String ^ progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   System::String ^ progid
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   const wchar_t * progid,
   LPUNKNOWN pouter
);
void CreateInstance(
   const wchar_t * progid
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter,
   DWORD cls_context
);
void CreateInstance(
   REFCLSID rclsid,
   LPUNKNOWN pouter
);
void CreateInstance(
   REFCLSID rclsid
);
```

### <a name="parameters"></a>Parametry

*progid*<br/>
A `ProgID` ciągu.

*pouter*<br/>
Wskaźnik interfejsu IUnknown obiektu agregacji (kontrolowanie IUnknown). Jeśli `pouter` nie jest określona, `NULL` jest używany.

*cls_context*<br/>
Kontekst, w którym będzie uruchamiany kod, który zarządza nowo utworzony obiekt. Wartości te są pobierane z `CLSCTX` wyliczenia. Jeśli `cls_context` nie jest określona, wartość CLSCTX_ALL jest używany.

*rclsid*<br/>
`CLSID` skojarzony z danymi i kod, który będzie używany do utworzenia obiektu.

### <a name="exceptions"></a>Wyjątki

Jeśli `com::ptr` już posiada odwołanie do obiektu COM `CreateInstance` zgłasza <xref:System.InvalidOperationException>.

Ta funkcja wywołuje `CoCreateInstance` i używa <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> do konwersji wszelkie błędy `HRESULT` na odpowiedni wyjątek.

### <a name="remarks"></a>Uwagi

`CreateInstance` używa `CoCreateInstance` do utworzenia nowego wystąpienia określonego obiektu, identyfikowany albo z identyfikator ProgID i CLSID. `com::ptr` Odwołuje się do nowo utworzonego obiektu i automatycznie zwolni wszystkich należących do odwołania na zniszczenia.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu. Konstruktory klasy użycie dwóch różnych metod `CreateInstance` można utworzyć obiektu dokumentu, z identyfikator ProgID albo z CLSID oraz CLSCTX.

```cpp
// comptr_createinstance.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }
   XmlDocument(REFCLSID clsid, DWORD clsctx) {
      m_ptrDoc.CreateInstance(clsid, NULL, clsctx);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc1("Msxml2.DOMDocument.3.0");

      // or from a clsid with specific CLSCTX
      XmlDocument doc2(CLSID_DOMDocument30, CLSCTX_INPROC_SERVER);
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

## <a name="detach"></a>ptr::Detach

Rezygnuje własności obiektu COM, zwraca wskaźnik do obiektu.

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu COM.

Jeśli żaden obiekt nie jest właścicielem, zwracana jest wartość NULL.

### <a name="exceptions"></a>Wyjątki

Wewnętrznie `QueryInterface` nosi nazwę na należących do obiektu COM i wszelkie błędy `HRESULT` jest konwertowana na wyjątek przez <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Uwagi

`Detach` najpierw dodaje odwołanie do obiektu COM w imieniu obiekt wywołujący i następnie zwalnia wszystkie odwołania własnością `com::ptr`.  Obiekt wywołujący musi zwolnić ostatecznie zwrócony obiekt do zniszczenia.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu.  `DetachDocument` Wywołania funkcji elementu członkowskiego `Detach` zrezygnować własności obiektu COM i zwracają wskaźnik do obiektu wywołującego.

```cpp
// comptr_detach.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // detach the COM object and return it
   // this releases the internal reference to the object
   IXMLDOMDocument* DetachDocument() {
      return m_ptrDoc.Detach();
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.DetachDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release document object as the ref class no longer owns it
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

## <a name="getInterface"></a>PTR::GetInterface

Zwraca wskaźnik do posiadanego obiektu COM.

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do posiadanego obiektu COM.

### <a name="exceptions"></a>Wyjątki

Wewnętrznie `QueryInterface` nosi nazwę na należących do obiektu COM i wszelkie błędy `HRESULT` jest konwertowana na wyjątek przez <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Uwagi

`com::ptr` Dodaje odwołanie do obiektu COM w imieniu wywołującego, a także zachowuje własne odwołanie do obiektu COM. Obiekt wywołujący musi ostatecznie Zwolnij odwołanie na zwracanym obiekcie lub nigdy nie zostaną usunięte.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu. `GetDocument` Funkcja członkowska używa `GetInterface` aby zwrócić wskaźnik do obiektu COM.

```cpp
// comptr_getinterface.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
            Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
            String^ strName = gcnew String(bstr);
            Console::Write("<{0}>", strName);
            ::SysFreeString(bstr);
            bstr = NULL;

            Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
            Console::Write(gcnew String(bstr));
            ::SysFreeString(bstr);
            bstr = NULL;

            Console::WriteLine("</{0}>", strName);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

```Output
<word>persnickety</word>
```

## <a name="queryInterface"></a>PTR::QueryInterface

Wykonuje kwerendę należących do obiektu COM dla interfejsu i dołącza wynik do innego `com::ptr`.

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>Parametry

*other*<br/>
`com::ptr` , Zostanie wyświetlony interfejs.

### <a name="exceptions"></a>Wyjątki

Wewnętrznie `QueryInterface` nosi nazwę na należących do obiektu COM i wszelkie błędy `HRESULT` jest konwertowana na wyjątek przez <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia utworzenie otoka COM dla innego interfejsu obiektu COM należące do bieżącego otoki. Ta metoda wywołuje `QueryInterface` za pośrednictwem obiektu COM należących do żądania wskaźnika z określonego interfejsu COM obiektu i dołącza wskaźnika interfejsu zwrócone do przekazanego `com::ptr`.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu. `WriteTopLevelNode` Funkcja członkowska używa `QueryInterface` do wypełnienia lokalnym `com::ptr` z `IXMLDOMNode` i następnie przekazuje `com::ptr` (przez odwołanie śledzenia) do funkcji prywatnego elementu członkowskiego, która zapisuje nazwę i tekstu — właściwości węzła do konsoli.

```cpp
// comptr_queryinterface.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   void LoadXml(String^ xml) {
      pin_ptr<const wchar_t> pinnedXml = PtrToStringChars(xml);
      BSTR bstr = NULL;

      try {
         // load some XML into our document
         bstr = ::SysAllocString(pinnedXml);
         if (NULL == bstr) {
            throw gcnew OutOfMemoryException;
         }
         VARIANT_BOOL bIsSuccessful = false;
         // use operator -> to call IXMODOMDocument member function
         Marshal::ThrowExceptionForHR(m_ptrDoc->loadXML(bstr, &bIsSuccessful));
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   // write the top level node to the console
   void WriteTopLevelNode() {
      com::ptr<IXMLDOMNode> ptrNode;

      // query for the top level node interface
      m_ptrDoc.QueryInterface(ptrNode);
      WriteNode(ptrNode);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   // simplified function that only writes the node
   void WriteNode(com::ptr<IXMLDOMNode> % node) {
      BSTR bstr = NULL;

      try {
         // write out the name and text properties
         Marshal::ThrowExceptionForHR(node->get_nodeName(&bstr));
         String^ strName = gcnew String(bstr);
         Console::Write("<{0}>", strName);
         ::SysFreeString(bstr);
         bstr = NULL;

         Marshal::ThrowExceptionForHR(node->get_text(&bstr));
         Console::Write(gcnew String(bstr));
         ::SysFreeString(bstr);
         bstr = NULL;

         Console::WriteLine("</{0}>", strName);
      }
      finally {
         ::SysFreeString(bstr);
      }
   }

   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // stream some xml into the document
      doc.LoadXml("<word>persnickety</word>");

      // write the document to the console
      doc.WriteTopLevelNode();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
<#document>persnickety</#document>
```

## <a name="release"></a>PTR::Release

Zwalnia wszystkie należące do firmy odwołania do obiektu COM.

```cpp
void Release();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji zwalnia wszystkie należące do firmy odwołania do obiektu COM, a następnie ustawia wewnętrzne dojście do obiektu COM, aby `nullptr`.  Jeśli istnieje nie inne odwołania do obiektu COM, zostaną usunięte.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu.  `ReplaceDocument` Funkcja członkowska używa `Release` zwolnić dowolnego obiektu poprzedniego dokumentu przed dołączeniem nowy dokument.

```cpp
// comptr_release.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc.Attach(pDoc);
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by our ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="operator-arrow"></a>PTR::operator, wartość —&gt;

Operator dostępu do elementu członkowskiego, używany do wywoływania metod na należących do obiektu COM.

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>Wartość zwracana

A `smart_com_ptr` do obiektu COM.

### <a name="exceptions"></a>Wyjątki

Wewnętrznie `QueryInterface` nosi nazwę na należących do obiektu COM i wszelkie błędy `HRESULT` jest konwertowana na wyjątek przez <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Uwagi

Ten operator umożliwia wywoływanie metod obiektu COM należące do firmy. Zwraca tymczasowego `smart_com_ptr` automatycznie obsługująca swój własny `AddRef` i `Release`.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu. `WriteDocument` Używa funkcji `operator->` do wywołania `get_firstChild` elementu członkowskiego obiektu dokumentu.

```cpp
// comptr_op_member.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // add a reference to and return the COM object
   // but keep an internal reference to the object
   IXMLDOMDocument* GetDocument() {
      return m_ptrDoc.GetInterface();
   }

   // simplified function that only writes the first node
   void WriteDocument() {
      IXMLDOMNode* pNode = NULL;
      BSTR bstr = NULL;

      try {
         // use operator -> to call XML Doc member
         Marshal::ThrowExceptionForHR(m_ptrDoc->get_firstChild(&pNode));
         if (NULL != pNode) {
            // write out the xml
            Marshal::ThrowExceptionForHR(pNode->get_nodeName(&bstr));
            String^ strName = gcnew String(bstr);
            Console::Write("<{0}>", strName);
            ::SysFreeString(bstr);
            bstr = NULL;

            Marshal::ThrowExceptionForHR(pNode->get_text(&bstr));
            Console::Write(gcnew String(bstr));
            ::SysFreeString(bstr);
            bstr = NULL;

            Console::WriteLine("</{0}>", strName);
         }
      }
      finally {
         if (NULL != pNode) {
            pNode->Release();
         }
         ::SysFreeString(bstr);
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that loads XML into a raw XML DOM Document object
HRESULT LoadXml(IXMLDOMDocument* pDoc, BSTR bstrXml) {
   HRESULT hr = S_OK;
   VARIANT_BOOL bSuccess;
   hr = pDoc->loadXML(bstrXml, &bSuccess);
   if (S_OK == hr && !bSuccess) {
      hr = E_FAIL;
   }
   return hr;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;
   BSTR bstrXml = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      bstrXml = ::SysAllocString(L"<word>persnickety</word>");
      if (NULL == bstrXml) {
         throw gcnew OutOfMemoryException("bstrXml");
      }
      // detach the document object from the ref class
      pDoc = doc.GetDocument();
      // use unmanaged function and raw object to load xml
      Marshal::ThrowExceptionForHR(LoadXml(pDoc, bstrXml));
      // release reference to document object (but ref class still references it)
      pDoc->Release();
      pDoc = NULL;

      // call another function on the ref class
      doc.WriteDocument();
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }

   }
}
```

```Output
<word>persnickety</word>
```

## <a name="operator-assign"></a>PTR::operator, wartość =

Dołącza do obiektów COM `com::ptr`.

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parametry

*_right*<br/>
Wskaźnik interfejsu COM do dołączenia.

### <a name="return-value"></a>Wartość zwracana

Odwołanie śledzenia na `com::ptr`.

### <a name="exceptions"></a>Wyjątki

Jeśli `com::ptr` już posiada odwołanie do obiektu COM `operator=` zgłasza <xref:System.InvalidOperationException>.

### <a name="remarks"></a>Uwagi

Przypisywanie obiektu COM, aby `com::ptr` odwołuje się do obiektu COM, ale nie zwalnia wywołującego odwołania do niego.

Ten operator ma taki sam skutek jak `Attach`.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu.  `ReplaceDocument` Wywołania pierwszej funkcji elementu członkowskiego `Release` na dowolnym wcześniej należały do obiektu, a następnie używa `operator=` można dołączyć nowy obiekt dokumentu.

```cpp
// comptr_op_assign.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // replace currently held COM object with another one
   void ReplaceDocument(IXMLDOMDocument* pDoc) {
      // release current document object
      m_ptrDoc.Release();
      // attach the new document object
      m_ptrDoc = pDoc;
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// unmanaged function that creates a raw XML DOM Document object
IXMLDOMDocument* CreateDocument() {
   IXMLDOMDocument* pDoc = NULL;
   Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
      CLSCTX_INPROC_SERVER, IID_IXMLDOMDocument, (void**)&pDoc));
   return pDoc;
}

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create the class from a progid string
      XmlDocument doc("Msxml2.DOMDocument.3.0");

      // get another document object from unmanaged function and
      // store it in place of the one held by the ref class
      pDoc = CreateDocument();
      doc.ReplaceDocument(pDoc);
      // no further need for raw object reference
      pDoc->Release();
      pDoc = NULL;
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="operator-bool"></a> PTR::operator, wartość logiczna

Operator przy użyciu `com::ptr` w wyrażeniu warunkowym.

```cpp
operator bool();
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli należących do obiektu COM są prawidłowe; `false` inaczej.

### <a name="remarks"></a>Uwagi

Należących do obiektu COM jest prawidłowa, jeśli nie jest `nullptr`.

Ten operator konwertuje `_detail_class::_safe_bool` co jest bezpieczniejszy niż `bool` , ponieważ nie można przekonwertować na typ całkowitoliczbowy.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu. `CreateInstance` Funkcja członkowska używa `operator bool` po utworzeniu nowego obiektu dokumentu, aby ustalić, czy jest prawidłowy i zapisuje do konsoli, jeśli jest.

```cpp
// comptr_op_bool.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   void CreateInstance(String^ progid) {
      if (!m_ptrDoc) {
         m_ptrDoc.CreateInstance(progid);
         if (m_ptrDoc) { // uses operator bool
            Console::WriteLine("DOM Document created.");
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      XmlDocument doc;
      // create the instance from a progid string
      doc.CreateInstance("Msxml2.DOMDocument.3.0");
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
DOM Document created.
```

## <a name="operator-logical-not"></a>PTR::operator, wartość!

Operator, aby określić, czy należących do obiektu COM jest nieprawidłowy.

```cpp
bool operator!();
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli należących do obiektu COM jest nieprawidłowa; `false` inaczej.

### <a name="remarks"></a>Uwagi

Należących do obiektu COM jest prawidłowa, jeśli nie jest `nullptr`.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu.  `CreateInstance` Funkcja członkowska używa `operator!` Aby ustalić, czy obiekt dokumentu ma już właściciela i tworzy nowe wystąpienie tylko, jeśli obiekt jest nieprawidłowy.

```cpp
// comptr_op_not.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   void CreateInstance(String^ progid) {
      if (!m_ptrDoc) {
         m_ptrDoc.CreateInstance(progid);
         if (m_ptrDoc) {
            Console::WriteLine("DOM Document created.");
         }
      }
   }

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   try {
      XmlDocument doc;
      // create the instance from a progid string
      doc.CreateInstance("Msxml2.DOMDocument.3.0");
   }
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
}
```

```Output
DOM Document created.
```
