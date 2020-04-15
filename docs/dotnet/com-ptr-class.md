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
ms.openlocfilehash: e494285f33cf282d7b7515aac374ec86ef3036b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372490"
---
# <a name="comptr-class"></a>com::ptr — Klasa

Otoka dla obiektu COM, który może służyć jako element członkowski klasy CLR.  Otoka automatyzuje również zarządzanie okresem istnienia obiektu COM, zwalniając wszystkie posiadane odwołania do obiektu, gdy wywoływany jest jego destruktor. Analogiczne do [klasy CComPtr](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Składnia

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>Parametry

*_interface_type*<br/>
interfejsu COM.

## <a name="remarks"></a>Uwagi

A `com::ptr` może być również używana jako lokalna zmienna funkcji w celu uproszczenia różnych zadań COM i zautomatyzowania zarządzania okresem istnienia.

A `com::ptr` nie może być używany bezpośrednio jako parametr funkcji; Zamiast tego użyj [operatora odwołania śledzenia](../extensions/tracking-reference-operator-cpp-component-extensions.md) lub operatora do obiektu Handle [(^).](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)

A `com::ptr` nie można zwrócić bezpośrednio z funkcji; zamiast tego użyj uchwytu.

## <a name="example"></a>Przykład

W tym przykładzie implementuje klasę `com::ptr` CLR, która `IXMLDOMDocument` używa do zawijania jego prywatnego obiektu członkowskiego.  Wywoływanie publicznych metod klasy powoduje wywołania `IXMLDOMDocument` do obiektu zawarte.  Przykład tworzy wystąpienie dokumentu XML, wypełnia go prostym kodem XML i wykonuje uproszczony spacer węzłów w drzewie analizowanych dokumentów w celu wydrukowania pliku XML na konsoli.

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

### <a name="public-constructors"></a>Konstruktorzy publiczni

|Nazwa|Opis|
|---------|-----------|
|[ptr::ptr](#ptr)|Konstruuje `com::ptr` a do zawijania com obiektu.|
|[ptr::~ptr](#tilde-ptr)|Niszczy . `com::ptr`|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|---------|-----------|
|[ptr::Attach](#attach)|Dołącza obiekt COM do `com::ptr`pliku .|
|[ptr::CreateInstance](#createInstance)|Tworzy wystąpienie obiektu COM `com::ptr`w obrębie pliku .|
|[ptr::Detach](#detach)|Rezygnuje z własności obiektu COM, zwracając wskaźnik do obiektu.|
|[ptr::GetInterface](#getInterface)|Tworzy wystąpienie obiektu COM `com::ptr`w obrębie pliku .|
|[ptr::QueryInterface](#queryInterface)|Wysyła kwerendy do należącego obiektu COM dla `com::ptr`interfejsu i dołącza wynik do innego .|
|[ptr::Release](#release)|Zwalnia wszystkie posiadane odwołania do obiektu COM.|

### <a name="public-operators"></a>Operatorzy publiczni

|Nazwa|Opis|
|---------|-----------|
|[ptr::operator-&gt;](#operator-arrow)|Operator dostępu do elementów członkowskich, używany do wywoływania metod na należącym do obiektu COM.|
|[ptr::operator=](#operator-assign)|Dołącza obiekt COM do `com::ptr`pliku .|
|[ptr::operator&nbsp;bool](#operator-bool)|Operator do `com::ptr` używania w wyrażeniu warunkowym.|
|[ptr::operator!](#operator-logical-not)|Operator, aby ustalić, czy należący do użytkownika obiekt COM jest nieprawidłowy.|

## <a name="requirements"></a>Wymagania

**Plik** \<nagłówka msclr\com\ptr.h>

**Msclr obszaru** nazw::com

## <a name="ptrptr"></a><a name="ptr"></a>ptr::ptr

Zwraca wskaźnik do należącego do obiektu COM.

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

Konstruktor bez argumentów `nullptr` przypisuje do dojścia obiektu źródłowego. Przyszłe wywołania `com::ptr` willa sprawdzania poprawności obiektu wewnętrznego i dyskretnie nie powiedzie się, dopóki obiekt nie zostanie utworzony lub dołączony.

Konstruktor jednego argumentu dodaje odwołanie do obiektu COM, ale nie zwalnia odwołania obiektu wywołującego, więc obiekt wywołujący musi wywołać `Release` obiekt COM, aby naprawdę zrezygnować z kontroli. `com::ptr`Po wywołaniu destruktora automatycznie zwolni swoje odwołania do obiektu COM.

Przekazywanie `NULL` do tego konstruktora jest taka sama jak wywołanie wersji bez argumentów.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę `com::ptr` CLR, która `IXMLDOMDocument` używa do zawijania jego prywatnego obiektu członkowskiego. Demonstruje użycie obu wersji konstruktora.

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

## <a name="ptrptr"></a><a name="tilde-ptr"></a>ptr::~ptr

Niszczy . `com::ptr`

```cpp
~ptr();
```

### <a name="remarks"></a>Uwagi

Po zniszczeniu `com::ptr` zwalnia wszystkie odwołania, których jest właścicielem do swojego obiektu COM. Zakładając, że nie ma żadnych innych odwołań przechowywanych do obiektu COM, obiekt COM zostanie usunięty, a jego pamięć zwolniona.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę `com::ptr` CLR, która `IXMLDOMDocument` używa do zawijania jego prywatnego obiektu członkowskiego.  W `main` funkcji destruktory dwóch `XmlDocument` obiektów zostaną wywołane, gdy wyjdą z zakresu `try` bloku, w wyniku czego wywoływany jest podstawowy `com::ptr` destruktor, zwalniając wszystkie posiadane odwołania do obiektu COM.

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

## <a name="ptrattach"></a><a name="attach"></a>ptr::Dołącz

Dołącza obiekt COM do `com::ptr`pliku .

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parametry

*_right*<br/>
Wskaźnik interfejsu COM do dołączenia.

### <a name="exceptions"></a>Wyjątki

Jeśli `com::ptr` posiada już odwołanie do obiektu `Attach` COM, zgłasza <xref:System.InvalidOperationException>.

### <a name="remarks"></a>Uwagi

Wywołanie `Attach` odwołuje się do obiektu COM, ale nie zwalnia odwołanie do obiektu wywołującego do niego.

Przejście `NULL` `Attach` do skutków nie jest podejmowane żadne działania.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę `com::ptr` CLR, która `IXMLDOMDocument` używa do zawijania jego prywatnego obiektu członkowskiego. Funkcja `ReplaceDocument` elementu członkowskiego `Release` najpierw wywołuje dowolny wcześniej `Attach` własnością obiektu, a następnie wywołuje dołączyć nowy obiekt dokumentu.

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

## <a name="ptrcreateinstance"></a><a name="createInstance"></a>ptr::Tworzenie instance

Tworzy wystąpienie obiektu COM `com::ptr`w obrębie pliku .

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
Ciąg. `ProgID`

*pouter*<br/>
Wskaźnik do agregacji obiektu IUnknown interfejsu (kontrolowanie IUnknown). Jeśli `pouter` nie jest `NULL` określony, jest używany.

*cls_context*<br/>
Kontekst, w którym zostanie uruchomiony kod, który zarządza nowo utworzonym obiektem. Wartości są pobierane `CLSCTX` z wyliczenia. Jeśli `cls_context` nie jest określony, używana jest wartość CLSCTX_ALL.

*rclsid ( rclsid )*<br/>
`CLSID`skojarzone z danymi i kodem, które będą używane do tworzenia obiektu.

### <a name="exceptions"></a>Wyjątki

Jeśli `com::ptr` posiada już odwołanie do obiektu `CreateInstance` COM, zgłasza <xref:System.InvalidOperationException>.

Ta funkcja `CoCreateInstance` wywołuje <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> i używa `HRESULT` do konwersji dowolnego błędu na odpowiedni wyjątek.

### <a name="remarks"></a>Uwagi

`CreateInstance`służy `CoCreateInstance` do tworzenia nowego wystąpienia określonego obiektu, zidentyfikowanego na podstawie identyfikatora ProgID lub IDENTYFIKATORA CLSID. Odwołuje `com::ptr` się do nowo utworzonego obiektu i automatycznie zwolni wszystkie posiadane odwołania po zniszczeniu.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę `com::ptr` CLR, która `IXMLDOMDocument` używa do zawijania jego prywatnego obiektu członkowskiego. Konstruktory klasy używają `CreateInstance` dwóch różnych form do tworzenia obiektu dokumentu z identyfikatora ProgID lub CLSID plus CLSCTX.

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

## <a name="ptrdetach"></a><a name="detach"></a>ptr::Detach

Rezygnuje z własności obiektu COM, zwracając wskaźnik do obiektu.

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu COM.

Jeśli żaden obiekt nie jest własnością, zwracana jest wartość NULL.

### <a name="exceptions"></a>Wyjątki

Wewnętrznie `QueryInterface` jest wywoływana na własnością obiektu `HRESULT` COM i każdy błąd <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>jest konwertowany na wyjątek przez .

### <a name="remarks"></a>Uwagi

`Detach`najpierw dodaje odwołanie do obiektu COM w imieniu obiektu wywołującego, a `com::ptr`następnie zwalnia wszystkie odwołania należące do obiektu .  Obiekt wywołujący musi ostatecznie zwolnić zwrócony obiekt, aby go zniszczyć.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę `com::ptr` CLR, która `IXMLDOMDocument` używa do zawijania jego prywatnego obiektu członkowskiego.  Funkcja `DetachDocument` elementu `Detach` członkowskiego wywołuje rezygnację z własności obiektu COM i zwraca wskaźnik do obiektu wywołującego.

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

## <a name="ptrgetinterface"></a><a name="getInterface"></a>ptr::GetInterface

Zwraca wskaźnik do należącego do obiektu COM.

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do należącego do obiektu COM.

### <a name="exceptions"></a>Wyjątki

Wewnętrznie `QueryInterface` jest wywoływana na własnością obiektu `HRESULT` COM i każdy błąd <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>jest konwertowany na wyjątek przez .

### <a name="remarks"></a>Uwagi

Dodaje `com::ptr` odwołanie do obiektu COM w imieniu obiektu wywołującego, a także zachowuje własne odwołanie do obiektu COM. Obiekt wywołujący musi ostatecznie zwolnić odwołanie na zwrócony obiekt lub nigdy nie zostaną zniszczone.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę `com::ptr` CLR, która `IXMLDOMDocument` używa do zawijania jego prywatnego obiektu członkowskiego. Funkcja `GetDocument` elementu członkowskiego `GetInterface` służy do zwracania wskaźnika do obiektu COM.

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

## <a name="ptrqueryinterface"></a><a name="queryInterface"></a>ptr::QueryInterface

Wysyła kwerendy do należącego obiektu COM dla `com::ptr`interfejsu i dołącza wynik do innego .

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Ten, `com::ptr` który otrzyma interfejs.

### <a name="exceptions"></a>Wyjątki

Wewnętrznie `QueryInterface` jest wywoływana na własnością obiektu `HRESULT` COM i każdy błąd <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>jest konwertowany na wyjątek przez .

### <a name="remarks"></a>Uwagi

Ta metoda służy do tworzenia otoki COM dla innego interfejsu obiektu COM należącego do bieżącego otoki. Ta metoda `QueryInterface` wywołuje za pośrednictwem należącego obiektu COM do żądania wskaźnika do określonego interfejsu obiektu `com::ptr`COM i dołącza zwrócony wskaźnik interfejsu do przekazanego.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę `com::ptr` CLR, która `IXMLDOMDocument` używa do zawijania jego prywatnego obiektu członkowskiego. Funkcja `WriteTopLevelNode` elementu członkowskiego `QueryInterface` służy do `com::ptr` wypełnienia `IXMLDOMNode` lokalnego, `com::ptr` a następnie przekazuje (przez odwołanie śledzenia) do funkcji prywatnego elementu członkowskiego, która zapisuje nazwę węzła i właściwości tekstu do konsoli.

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

## <a name="ptrrelease"></a><a name="release"></a>ptr::Zwolnij

Zwalnia wszystkie posiadane odwołania do obiektu COM.

```cpp
void Release();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji zwalnia wszystkie posiadane odwołania do obiektu COM `nullptr`i ustawia wewnętrzny uchwyt na obiekt COM .  Jeśli nie istnieją żadne inne odwołania do obiektu COM, zostanie on zniszczony.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę `com::ptr` CLR, która `IXMLDOMDocument` używa do zawijania jego prywatnego obiektu członkowskiego.  Funkcja `ReplaceDocument` elementu członkowskiego `Release` służy do zwalniania dowolnego wcześniejszego obiektu dokumentu przed załączeniem nowego dokumentu.

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

## <a name="ptroperator-gt"></a><a name="operator-arrow"></a>ptr::operator-&gt;

Operator dostępu do elementów członkowskich, używany do wywoływania metod na należącym do obiektu COM.

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>Wartość zwracana

A `smart_com_ptr` do obiektu COM.

### <a name="exceptions"></a>Wyjątki

Wewnętrznie `QueryInterface` jest wywoływana na własnością obiektu `HRESULT` COM i każdy błąd <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>jest konwertowany na wyjątek przez .

### <a name="remarks"></a>Uwagi

Ten operator umożliwia wywoływanie metod należącego do obiektu COM. Zwraca tymczasowy, `smart_com_ptr` który automatycznie obsługuje `AddRef` własne `Release`i .

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę `com::ptr` CLR, która `IXMLDOMDocument` używa do zawijania jego prywatnego obiektu członkowskiego. Funkcja `WriteDocument` służy `operator->` do wywoływania `get_firstChild` elementu członkowskiego obiektu dokumentu.

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

## <a name="ptroperator"></a><a name="operator-assign"></a>ptr::operator=

Dołącza obiekt COM do `com::ptr`pliku .

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parametry

*_right*<br/>
Wskaźnik interfejsu COM do dołączenia.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do śledzenia `com::ptr`na pliku .

### <a name="exceptions"></a>Wyjątki

Jeśli `com::ptr` posiada już odwołanie do obiektu `operator=` COM, zgłasza <xref:System.InvalidOperationException>.

### <a name="remarks"></a>Uwagi

Przypisywanie obiektu COM `com::ptr` do obiektu COM odwołuje się do obiektu COM, ale nie zwalnia odwołania do niego.

Ten operator ma taki `Attach`sam efekt jak .

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę `com::ptr` CLR, która `IXMLDOMDocument` używa do zawijania jego prywatnego obiektu członkowskiego.  Funkcja `ReplaceDocument` elementu członkowskiego `Release` najpierw wywołuje dowolny wcześniej własnością `operator=` obiektu, a następnie używa do dołączenia nowego obiektu dokumentu.

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

## <a name="ptroperator-bool"></a><a name="operator-bool"></a>ptr::operator bool

Operator do `com::ptr` używania w wyrażeniu warunkowym.

```cpp
operator bool();
```

### <a name="return-value"></a>Wartość zwracana

`true`jeśli należący do obiektu COM jest prawidłowy; `false` w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Należący do niego obiekt COM jest `nullptr`prawidłowy, jeśli nie jest .

Ten operator konwertuje `_detail_class::_safe_bool` do `bool` którego jest bezpieczniejsze niż dlatego, że nie można przekonwertować na typ integralną.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę `com::ptr` CLR, która `IXMLDOMDocument` używa do zawijania jego prywatnego obiektu członkowskiego. Funkcja `CreateInstance` elementu członkowskiego `operator bool` używa po utworzeniu nowego obiektu dokumentu, aby określić, czy jest prawidłowy i zapisuje w konsoli, jeśli jest.

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

## <a name="ptroperator"></a><a name="operator-logical-not"></a>ptr::operator!

Operator, aby ustalić, czy należący do użytkownika obiekt COM jest nieprawidłowy.

```cpp
bool operator!();
```

### <a name="return-value"></a>Wartość zwracana

`true`jeśli należący do obiektu COM jest nieprawidłowy; `false` w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Należący do niego obiekt COM jest `nullptr`prawidłowy, jeśli nie jest .

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę `com::ptr` CLR, która `IXMLDOMDocument` używa do zawijania jego prywatnego obiektu członkowskiego.  Funkcja `CreateInstance` elementu członkowskiego `operator!` służy do określenia, czy obiekt dokumentu jest już własnością i tworzy nowe wystąpienie tylko wtedy, gdy obiekt jest nieprawidłowy.

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
