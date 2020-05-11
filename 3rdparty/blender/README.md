This library is gotten from https://formats.kaitai.io/blender_blend/cpp_stl.html and is under the MIT license.

Some instructions:

We need to create an STL input stream (std::istream). One can open local file for that, or use existing std::string or char* buffer.

From local file
===============

    #include <fstream>

    std::ifstream is("path/to/local/file.blend", std::ifstream::binary);

We need to wrap our input stream into Kaitai stream:

    #include <kaitai/kaitaistream.h>

    kaitai::kstream ks(&is);

And finally, we can invoke the parsing:

    blender_blend_t data(&ks);

From std::string
================

    #include <sstream>

    std::istringstream is(str);

From char*
==========

    #include <sstream>

    const char buf[] = { ... };
    std::string str(buf, sizeof buf);
    std::istringstream is(str);

Then
====

After that, one can get various attributes from the structure by invoking getter methods like:

    data.hdr() // => get hdr