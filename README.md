# public


All original material created by Barry Alan Feigenbaum, Ph.D..

Copyright (C) Barry Alan Feigenbaum. 2016.

Any derived work (based on the Apache 2.0 license or not) must retain (shown in any derived source) this copyright.  

Summary of included projects:
 * JSON Utilities (AKA JSONutils).  A simple Java library to process JSON text in a JRE. 



#JSONUtils

Expand JSONutils.jar to get contents. See the associated README.html file and the included JavaDoc for more details. 

This is a light-weight implementation built on the existing *List* and *Map* types (for minimal impedence mismatch with JRE types). 

It supports easy conversion between standard JRE types and JSON strings via conversion between *JsonValue*s (base interface of all JSON types: *JsonNull*, *JsonBoolean*, *JsonString*, *JsonNumber*, *JsonArray* and *JsonObject*) and JSON strings.
JsonArrays and JsonObjects are type-safe (may only have JsonValues (or equivalent native JRE types) as members).

It supports serialization of JsonValues to either JSON text or to a byte stream (often smaller than equivalent JSON strings). 

An example:

`

    public void asXxxTest1() {
        JsonObject o1 = JsonObject.asObject("1", 1, "2", 2, "3", 3);
        JsonObject to1 = new JsonObject();
        to1.put("1", 1);
        to1.put("2", 2);
        to1.put("3", 3);
        assertTrue("equal object", o1.equals(to1));

        JsonArray a1 = JsonArray.asArray("1", 1, "2", 2, "3", 3, JsonArray.asArray(1, 2, 3));
        JsonArray ta1 = new JsonArray();
        ta1.add("1");  // same as ta1.add(new JsonString("1")); 
        ta1.add(1);    // same as ta1.add(new JsonNumber(1));
        ta1.add("2");
        ta1.add(2);
        ta1.add("3");
        ta1.add(3);
        JsonArray ta2 = new JsonArray();
        ta1.add(ta2);
        ta2.add(1);
        ta2.add(2);
        ta2.add(3);
        assertTrue("equal array", a1.equals(ta1));
    }
`
