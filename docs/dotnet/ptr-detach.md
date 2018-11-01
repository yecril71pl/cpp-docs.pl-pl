---
title: ptr::Detach
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ptr.Detach
- msclr.com.ptr.Detach
- ptr::Detach
- msclr::com::ptr::Detach
helpviewer_keywords:
- ptr::Detach
ms.assetid: 23370c8a-8f79-4880-9fa1-46e110c1a92c
ms.openlocfilehash: 1b8ebd44cad7853415856594b523f8d70039d371
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445126"
---
# <a name="ptrdetach"></a>ptr::Detach

Rezygnuje własności obiektu COM, zwraca wskaźnik do obiektu.

## <a name="syntax"></a>Składnia

```
_interface_type * Detach();
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu COM.

Jeśli żaden obiekt nie jest właścicielem, zwracana jest wartość NULL.

## <a name="exceptions"></a>Wyjątki

Wewnętrznie `QueryInterface` nosi nazwę na należących do obiektu COM i wszelkie błędy `HRESULT` jest konwertowana na wyjątek przez <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>.

## <a name="remarks"></a>Uwagi

`Detach` najpierw dodaje odwołanie do obiektu COM w imieniu obiekt wywołujący i następnie zwalnia wszystkie odwołania własnością `com::ptr`.  Obiekt wywołujący musi zwolnić ostatecznie zwrócony obiekt do zniszczenia.

## <a name="example"></a>Przykład

W tym przykładzie implementuje klasę CLR, która używa `com::ptr` opakowywać jej prywatnego elementu członkowskiego `IXMLDOMDocument` obiektu.  `DetachDocument` Wywołania funkcji elementu członkowskiego `Detach` zrezygnować własności obiektu COM i zwracają wskaźnik do obiektu wywołującego.

```
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

## <a name="requirements"></a>Wymagania

**Plik nagłówkowy** \<msclr\com\ptr.h >

**Namespace** msclr::com

## <a name="see-also"></a>Zobacz też

[ptr, składowe](../dotnet/ptr-members.md)<br/>
[ptr::Release](../dotnet/ptr-release.md)<br/>
[ptr::Attach](../dotnet/ptr-attach.md)