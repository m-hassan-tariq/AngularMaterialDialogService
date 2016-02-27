# Angular Material Dialog Service
Custom dialog service using Angular Material 

Customize Angular dialogue service, register within your controller and other data services and use it throughout your project.

Angular Code:

    (function () {
        'use strict';
    
        var app = angular.module('app', ['ngMaterial']);
    
        app.controller('dialogController', function (confirmAlert) {
    
            var vm = this;
            
            vm.confirm= function () {
                confirmAlert.confirmBoxResponse(
                    'Would you like to delete?',
                    'Record will be deleted ',
                    'Delete',
                    callBack,
                    "Hello World");
            };
    
            function callBack(param) {
                vm.result = param;
            }
    
        });
    
    })();

Toaster Service:

    (function () {
        'use strict';
    
        angular
            .module('app')
            .factory('confirmAlert', confirmAlert);
    
        confirmAlert.$inject = ['$mdDialog'];
    
        function confirmAlert($mdDialog) {
    
            var service = {
                confirmBoxResponse: confirmBoxResponse
            };
    
            return service;
    
            ////////////////////////////Implementation//////////////////////////////////////
    
            function confirmBoxResponse(title, content, confirmText, successCb, successCbParam) {
                var confirm = $mdDialog.confirm()
                          .title(title)
                          .textContent(content)
                          .ariaLabel('Lucky day')
                          .ok(confirmText)
                          .cancel('Cancel');
    
                $mdDialog.show(confirm).then(function () {
                    successCb(successCbParam);
                }, function () {
                    //pressed cancel
                });
            }
    
        }
    
    })();

Output:

![screenshot_2](https://cloud.githubusercontent.com/assets/10474169/13370529/b2116e30-dccf-11e5-99cc-7605e3676ec7.png)
