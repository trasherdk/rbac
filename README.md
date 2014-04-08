# RBAC (Hierarchical Role Based Access Control)

[![Quality](https://codeclimate.com/github/seeden/rbac.png)](https://codeclimate.com/github/seeden/rbac/badges)
[![Dependencies](https://david-dm.org/seeden/rbac.png)](https://david-dm.org/seeden/rbac)

RBAC is the authorization library for NodeJs. 


## Install

    $ npm install rbac


## Usage

    var RBAC = require('rbac');

    //create instance of RBAC
    var rbac = new RBAC();

    //create permissions
    var createArticle = rbac.createPermission('create', 'article');
    var deleteUser = rbac.createPermission('delete', 'user');

    //create roles
    var admin = rbac.createRole('admin');
    var user = rbac.createRole('user');

    //assign permissions to roles
    user.allow(createArticle);
    admin.allow(deleteUser);
    
    //create hierarchy
    admin.allow(user);

    //check permissions
    var isAllowed = admin.isAllowed('create', 'article');
    var isAllowed = user.isAllowed('delete', 'user');

    
## Credits

  - [Zlatko Fedor](http://github.com/seeden)

## License

[The MIT License](http://opensource.org/licenses/MIT)

Copyright (c) 2014 Zlatko Fedor <[http://www.cherrysro.com/](http://www.cherrysro.com/)>