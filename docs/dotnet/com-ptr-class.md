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
ms.openlocfilehash: 8a3223543dfa6c1b5b45fef2780cd11b558eab84
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078962"
---
# <a name="comptr-class"></a>com::ptr — Klasa

Otoka dla obiektu COM, który może być używany jako element członkowski klasy CLR.  Otoka również automatyzuje zarządzanie czasem istnienia obiektu COM, zwalniając wszystkie odwołania do obiektu, gdy jego destruktor jest wywoływany. Analogiczne do [klasy CComPtr](../atl/reference/ccomptr-class.md).

## <a name="syntax"></a>Składnia

```
template<class _interface_type>
ref class ptr;
```

### <a name="parameters"></a>Parametry

*_interface_type*<br/>
Interfejs COM.

## <a name="remarks"></a>Uwagi

`com::ptr` może być również używana jako zmienna funkcji lokalnych w celu uproszczenia różnych zadań COM i zautomatyzowania zarządzania okresem istnienia.

`com::ptr` nie może być używana bezpośrednio jako parametr funkcji; Zamiast tego użyj [operatora odwołania śledzącego](../extensions/tracking-reference-operator-cpp-component-extensions.md) lub [uchwytu do operatora obiektu (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) .

Nie można bezpośrednio zwrócić `com::ptr` z funkcji; Zamiast tego użyj dojścia.

## <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr`, aby otoczyć swój prywatny element członkowski `IXMLDOMDocument` obiektu.  Wywołanie metod publicznych klasy skutkuje wywołaniami zawartego obiektu `IXMLDOMDocument`.  Przykład tworzy wystąpienie dokumentu XML, wypełnia go niezwykłym kodem XML i uproszczone przeszukiwanie węzłów w drzewie przeanalizowanych dokumentów, aby wydrukować XML do konsoli.

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

|Name (Nazwa)|Opis|
|---------|-----------|
|[ptr::ptr](#ptr)|Konstruuje `com::ptr` do zawijania obiektu COM.|
|[ptr::~ptr](#tilde-ptr)|Destruktory `com::ptr`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|---------|-----------|
|[ptr::Attach](#attach)|Dołącza obiekt COM do `com::ptr`.|
|[ptr::CreateInstance](#createInstance)|Tworzy wystąpienie obiektu COM w `com::ptr`.|
|[ptr::Detach](#detach)|Zwraca własność obiektu COM, zwracając wskaźnik do obiektu.|
|[ptr::GetInterface](#getInterface)|Tworzy wystąpienie obiektu COM w `com::ptr`.|
|[ptr::QueryInterface](#queryInterface)|Wysyła zapytanie do obiektu COM należącego do interfejsu i dołącza wynik do innego `com::ptr`.|
|[ptr::Release](#release)|Zwalnia wszystkie odwołania należące do obiektu COM.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|---------|-----------|
|[PTR:: operator-&gt;](#operator-arrow)|Operator dostępu do elementów członkowskich używany do wywoływania metod w obiekcie COM należącym do użytkownika.|
|[ptr::operator=](#operator-assign)|Dołącza obiekt COM do `com::ptr`.|
|[PTR:: operator&nbsp;bool](#operator-bool)|Operator służący do używania `com::ptr` w wyrażeniu warunkowym.|
|[ptr::operator!](#operator-logical-not)|Operatora, aby określić, czy właścicielem obiektu COM jest nieprawidłowy.|

## <a name="requirements"></a>Wymagania

**Plik nagłówka** \<msclr\com\ptr.h >

**Przestrzeń nazw** msclr:: com

## <a name="ptrptr"></a><a name="ptr"></a>PTR::p TR

Zwraca wskaźnik do posiadanego obiektu COM.

```cpp
ptr();
ptr(
   _interface_type * p
);
```

### <a name="parameters"></a>Parametry

*St*<br/>
Wskaźnik interfejsu COM.

### <a name="remarks"></a>Uwagi

Konstruktor bez argumentów przypisuje `nullptr` do uchwytu bazowego obiektu. Przyszłe wywołania `com::ptr` będą sprawdzać poprawność obiektu wewnętrznego i dyskretnie kończyć się niepowodzeniem do momentu utworzenia lub dołączenia obiektu.

Konstruktor z jednym argumentem dodaje odwołanie do obiektu COM, ale nie zwalnia odwołania wywołującego, więc obiekt wywołujący musi wywoływać `Release` w obiekcie COM, aby w rzeczywistości przekazać kontrolę. Gdy zostanie wywołany destruktor `com::ptr`, automatycznie zwolni swoje odwołania do obiektu COM.

Przekazywanie `NULL` do tego konstruktora jest takie samo jak wywołanie wersji bez argumentów.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr`, aby otoczyć swój prywatny element członkowski `IXMLDOMDocument` obiektu. Ilustruje on użycie obu wersji konstruktora.

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

## <a name="ptrptr"></a><a name="tilde-ptr"></a>PTR:: ~ PTR

Destruktory `com::ptr`.

```cpp
~ptr();
```

### <a name="remarks"></a>Uwagi

W przypadku zniszczenia `com::ptr` wszystkie odwołania do niego należy do obiektu COM. Przy założeniu, że nie istnieją żadne inne odwołania do obiektu COM, obiekt COM zostanie usunięty, a jego pamięć jest zwolniona.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr`, aby otoczyć swój prywatny element członkowski `IXMLDOMDocument` obiektu.  W funkcji `main` dwa destruktory obiektów `XmlDocument` są wywoływane, gdy stają się poza zakresem bloku `try`, co spowoduje wywołanie podstawowego destruktora `com::ptr`, zwalniając wszystkie odwołania do obiektu COM.

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

## <a name="ptrattach"></a><a name="attach"></a>PTR:: Attach

Dołącza obiekt COM do `com::ptr`.

```cpp
void Attach(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parametry

*_right*<br/>
Wskaźnik interfejsu COM do dołączenia.

### <a name="exceptions"></a>Wyjątki

Jeśli `com::ptr` już jest odwołaniem do obiektu COM, `Attach` zgłasza <xref:System.InvalidOperationException>.

### <a name="remarks"></a>Uwagi

Wywołanie `Attach` odwołuje się do obiektu COM, ale nie zwalnia odwołania do niego.

Przekazanie `NULL` do `Attach` powoduje, że nie są podejmowane żadne akcje.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr`, aby otoczyć swój prywatny element członkowski `IXMLDOMDocument` obiektu. `ReplaceDocument` funkcja członkowska najpierw wywołuje `Release` dla każdego poprzednio należącego do niego obiektu, a następnie wywołuje `Attach` w celu dołączenia nowego obiektu dokumentu.

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

## <a name="ptrcreateinstance"></a><a name="createInstance"></a>PTR:: CreateInstance

Tworzy wystąpienie obiektu COM w `com::ptr`.

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
Ciąg `ProgID`.

*pouter*<br/>
Wskaźnik do interfejsu IUnknown obiektu zagregowanego (kontrolka IUnknown). Jeśli `pouter` nie jest określony, używany jest `NULL`.

*cls_context*<br/>
Kontekst, w którym zostanie uruchomiony kod zarządzający nowo utworzonym obiektem. Wartości są pobierane z wyliczenia `CLSCTX`. Jeśli `cls_context` nie jest określony, zostanie użyta wartość CLSCTX_ALL.

*rclsid*<br/>
`CLSID` skojarzona z danymi i kodem, który zostanie użyty do utworzenia obiektu.

### <a name="exceptions"></a>Wyjątki

Jeśli `com::ptr` już jest odwołaniem do obiektu COM, `CreateInstance` zgłasza <xref:System.InvalidOperationException>.

Ta funkcja wywołuje `CoCreateInstance` i używa <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> do konwertowania dowolnego błędu `HRESULT` na odpowiedni wyjątek.

### <a name="remarks"></a>Uwagi

`CreateInstance` używa `CoCreateInstance`, aby utworzyć nowe wystąpienie określonego obiektu, identyfikowane za pomocą identyfikatora ProgID lub CLSID. `com::ptr` odwołuje się do nowo utworzonego obiektu i automatycznie zwolni wszystkie posiadane odwołania po zniszczeniu.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr`, aby otoczyć swój prywatny element członkowski `IXMLDOMDocument` obiektu. Konstruktory klas używają dwóch różnych form `CreateInstance` do tworzenia obiektu dokumentu z identyfikatora ProgID lub z identyfikatora CLSID i CLSCTX.

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

## <a name="ptrdetach"></a><a name="detach"></a>PTR::D etach

Zwraca własność obiektu COM, zwracając wskaźnik do obiektu.

```cpp
_interface_type * Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu COM.

Jeśli żaden obiekt nie należy do użytkownika, zwracana jest wartość NULL.

### <a name="exceptions"></a>Wyjątki

Wewnętrznie, `QueryInterface` jest wywoływana w obiekcie COM należącym do użytkownika, a wszystkie `HRESULT` błędów są konwertowane na wyjątek przez <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Uwagi

`Detach` najpierw dodaje odwołanie do obiektu COM w imieniu obiektu wywołującego, a następnie zwalnia wszystkie odwołania należące do `com::ptr`.  Obiekt wywołujący musi ostatecznie zwolnić zwrócony obiekt, aby zniszczyć go.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr`, aby otoczyć swój prywatny element członkowski `IXMLDOMDocument` obiektu.  Funkcja elementu członkowskiego `DetachDocument` wywołuje `Detach`, aby przyznać własności obiektu COM i zwrócić wskaźnik do wywołującego.

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

## <a name="ptrgetinterface"></a><a name="getInterface"></a>PTR:: GetInterface

Zwraca wskaźnik do posiadanego obiektu COM.

```cpp
_interface_type * GetInterface();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do posiadanego obiektu COM.

### <a name="exceptions"></a>Wyjątki

Wewnętrznie, `QueryInterface` jest wywoływana w obiekcie COM należącym do użytkownika, a wszystkie `HRESULT` błędów są konwertowane na wyjątek przez <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Uwagi

`com::ptr` dodaje odwołanie do obiektu COM w imieniu obiektu wywołującego, a także zachowuje własne odwołanie do obiektu COM. Obiekt wywołujący musi ostatecznie zwolnić odwołanie do zwróconego obiektu lub nigdy nie zostanie zniszczony.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr`, aby otoczyć swój prywatny element członkowski `IXMLDOMDocument` obiektu. Funkcja członkowska `GetDocument` używa `GetInterface` do zwrócenia wskaźnika do obiektu COM.

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

## <a name="ptrqueryinterface"></a><a name="queryInterface"></a>PTR:: QueryInterface

Wysyła zapytanie do obiektu COM należącego do interfejsu i dołącza wynik do innego `com::ptr`.

```cpp
template<class _other_type>
void QueryInterface(
   ptr<_other_type> % other
);
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
`com::ptr`, który pobierze interfejs.

### <a name="exceptions"></a>Wyjątki

Wewnętrznie, `QueryInterface` jest wywoływana w obiekcie COM należącym do użytkownika, a wszystkie `HRESULT` błędów są konwertowane na wyjątek przez <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Uwagi

Ta metoda służy do tworzenia otoki COM dla innego interfejsu obiektu COM należącego do bieżącej otoki. Ta metoda wywołuje `QueryInterface` za pomocą należącego do siebie obiektu COM, aby zażądać wskaźnika do określonego interfejsu obiektu COM i dołączył zwrócony wskaźnik interfejsu do `com::ptr`przekazana.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr`, aby otoczyć swój prywatny element członkowski `IXMLDOMDocument` obiektu. Funkcja członkowska `WriteTopLevelNode` używa `QueryInterface` do wypełnienia `com::ptr` lokalnego przy użyciu `IXMLDOMNode`, a następnie przekazuje `com::ptr` (przez odwołanie śledzące) do funkcji prywatnego elementu członkowskiego, która zapisuje nazwę węzła i właściwości tekstu w konsoli programu.

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

## <a name="ptrrelease"></a><a name="release"></a>PTR:: Release

Zwalnia wszystkie odwołania należące do obiektu COM.

```cpp
void Release();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji zwalnia wszystkie odwołania należące do obiektu COM i ustawia wewnętrzne dojście do obiektu COM, aby `nullptr`.  Jeśli żadne inne odwołanie do obiektu COM nie istnieje, zostanie zniszczone.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr`, aby otoczyć swój prywatny element członkowski `IXMLDOMDocument` obiektu.  Funkcja członkowska `ReplaceDocument` używa `Release` do zwolnienia dowolnego obiektu dokumentu przed dołączeniem nowego dokumentu.

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

## <a name="ptroperator-gt"></a><a name="operator-arrow"></a>PTR:: operator-&gt;

Operator dostępu do elementów członkowskich używany do wywoływania metod w obiekcie COM należącym do użytkownika.

```cpp
_detail::smart_com_ptr<_interface_type> operator->();
```

### <a name="return-value"></a>Wartość zwracana

`smart_com_ptr` do obiektu COM.

### <a name="exceptions"></a>Wyjątki

Wewnętrznie, `QueryInterface` jest wywoływana w obiekcie COM należącym do użytkownika, a wszystkie `HRESULT` błędów są konwertowane na wyjątek przez <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

### <a name="remarks"></a>Uwagi

Ten operator umożliwia wywoływanie metod obiektu COM. Zwraca tymczasowy `smart_com_ptr`, który automatycznie obsługuje własne `AddRef` i `Release`.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr`, aby otoczyć swój prywatny element członkowski `IXMLDOMDocument` obiektu. Funkcja `WriteDocument` używa `operator->` do wywoływania `get_firstChild` elementu członkowskiego obiektu dokumentu.

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

## <a name="ptroperator"></a><a name="operator-assign"></a>PTR:: operator =

Dołącza obiekt COM do `com::ptr`.

```cpp
ptr<_interface_type> % operator=(
   _interface_type * _right
);
```

### <a name="parameters"></a>Parametry

*_right*<br/>
Wskaźnik interfejsu COM do dołączenia.

### <a name="return-value"></a>Wartość zwracana

Odwołanie śledzące na `com::ptr`.

### <a name="exceptions"></a>Wyjątki

Jeśli `com::ptr` już jest odwołaniem do obiektu COM, `operator=` zgłasza <xref:System.InvalidOperationException>.

### <a name="remarks"></a>Uwagi

Przypisanie obiektu COM do `com::ptr` odwołuje się do obiektu COM, ale nie zwalnia odwołania do niego.

Ten operator ma ten sam skutek co `Attach`.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr`, aby otoczyć swój prywatny element członkowski `IXMLDOMDocument` obiektu.  Funkcja elementu członkowskiego `ReplaceDocument` najpierw wywołuje `Release` dla każdego poprzednio należącego do niego obiektu, a następnie używa `operator=` do dołączania nowego obiektu dokumentu.

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

## <a name="ptroperator-bool"></a><a name="operator-bool"></a>PTR:: operator — bool

Operator służący do używania `com::ptr` w wyrażeniu warunkowym.

```cpp
operator bool();
```

### <a name="return-value"></a>Wartość zwracana

`true`, Jeśli właścicielem obiektu COM jest prawidłowy; `false` w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Obiekt modelu COM jest prawidłowy, jeśli nie jest `nullptr`.

Ten operator konwertuje do `_detail_class::_safe_bool`, który jest bezpieczniejszy niż `bool`, ponieważ nie można go przekonwertować na typ całkowity.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr`, aby otoczyć swój prywatny element członkowski `IXMLDOMDocument` obiektu. Funkcja członkowska `CreateInstance` używa `operator bool` po utworzeniu nowego obiektu dokumentu w celu ustalenia, czy jest on prawidłowy, i zapisuje w konsoli, jeśli jest.

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

## <a name="ptroperator"></a><a name="operator-logical-not"></a>PTR:: operator!

Operatora, aby określić, czy właścicielem obiektu COM jest nieprawidłowy.

```cpp
bool operator!();
```

### <a name="return-value"></a>Wartość zwracana

`true`, Jeśli właścicielem obiektu COM jest nieprawidłowy; `false` w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Obiekt modelu COM jest prawidłowy, jeśli nie jest `nullptr`.

### <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr`, aby otoczyć swój prywatny element członkowski `IXMLDOMDocument` obiektu.  Funkcja członkowska `CreateInstance` używa `operator!`, aby określić, czy obiekt dokumentu jest już własnością, i tylko tworzy nowe wystąpienie, jeśli obiekt jest nieprawidłowy.

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
