Axioms is kind of unit test. Its collects live data of type and apply data to axiom's fn in random order. If test is failed - throw {AxiomFailedError}. Its direct interpretation of math axiom and generally used in math types such as AddAbelianGroup
<pre>    
    my AddGroupoid = slice {
      operator('x += y') (){ abstract }
    }
    my AddSemiGroup = slice limits(AddGroupoid) {
      axiom (a: Self, b: Self, c: Self){ -> (a + b) + c == a + (b + c) }  
    }
    my AddMonoid = slice limits(AddGroupoid) {
      get zero() -> MasterSlice { abstract }
    }
    my String = slice implements(AddMonoid) {
      implement operator('x += y') (y: MasterSlice) { ... }
      implement get zero() { ... }
    }
    my CString = class implements(String) { ... }
    
    my a = '1' // axiom(a, a, a)
    my b = '2' // axiom(a, a, b)
    my c = '3' // axiom(a, b, c)
    my d = '4' // axiom(b, c, d)
</pre>    