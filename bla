'use strict';

require("./env");

var Connection = require('tedious').Connection;
var Request = require('tedious').Request;

if(!process.env.MSSQL_HOST) {
    throw new Error('No Environment variable MSSQL_HOST provided');
}

if(!global.mssqlConnection) {
    global.mssqlConnection = new Connection(getMSSQLConnectionOptions());
    global.mssqlConnected = new Promise(function(resolve, reject) {
        global.mssqlConnection.on('connect', function(err) {
            if(err) {
                reject(err);
            } else {
                resolve();
            }
        });
        global.mssqlConnection.on('error', reject);
    });
} else {
    console.log('Re-Using MSSQL connection');
}

var connection = global.mssqlConnection;
var connected = global.mssqlConnected;

var query = function(queries: string[]): any {

    if(typeof queries === 'string') {
        queries = queries;
    }

    var queryString = queries.shift();

    return connected.then(function() {
         
        var q = new Promise(function(resolve, reject) {

            var request = new Request(queryString, function(err, rowCount, rows) {

                if(err) {
                    return reject(err);
                }

                var outRows = [];

                rows.forEach(function(row) {
                    var outRow = {};
                    row.forEach(function(column) {
                        outRow[column.metadata.colName] = column.value;
                    })

                    outRows.push(outRow);
                });

                resolve({
                    rows: outRows,
                    rowCount: rowCount
                });

            });

            connection.execSql(request);
        });

        if(queries.length) {
            return q.then(function() {
                return query(queries);
            });
        } else {
            return q;
        }

    });

};

export { query };

function getMSSQLConnectionOptions() {

    //example MSSQL_HOST=mku1xoy51v.database.windows.net:1433
    var host: string = process.env.MSSQL_HOST;
    var hostMatch: RegExpMatchArray = host.match(/^([^:]+)(?:[:]([0-9]+))?$/);

    var connectionOptions = {
        server: hostMatch[1],
        userName: "bla",
        password: "'use strict';

require("./env");

var Connection = require('tedious').Connection;
var Request = require('tedious').Request;

if(!process.env.MSSQL_HOST) {
    throw new Error('No Environment variable MSSQL_HOST provided');
}

if(!global.mssqlConnection) {
    global.mssqlConnection = new Connection(getMSSQLConnectionOptions());
    global.mssqlConnected = new Promise(function(resolve, reject) {
        global.mssqlConnection.on('connect', function(err) {
            if(err) {
                reject(err);
            } else {
                resolve();
            }
        });
        global.mssqlConnection.on('error', reject);
    });
} else {
    console.log('Re-Using MSSQL connection');
}

var connection = global.mssqlConnection;
var connected = global.mssqlConnected;

var query = function(queries: string[]): any {

    if(typeof queries === 'string') {
        queries = queries;
    }

    var queryString = queries.shift();

    return connected.then(function() {
         
        var q = new Promise(function(resolve, reject) {

            var request = new Request(queryString, function(err, rowCount, rows) {

                if(err) {
                    return reject(err);
                }

                var outRows = [];

                rows.forEach(function(row) {
                    var outRow = {};
                    row.forEach(function(column) {
                        outRow[column.metadata.colName] = column.value;
                    })

                    outRows.push(outRow);
                });

                resolve({
                    rows: outRows,
                    rowCount: rowCount
                });

            });

            connection.execSql(request);
        });

        if(queries.length) {
            return q.then(function() {
                return query(queries);
            });
        } else {
            return q;
        }

    });

};

export { query };

function getMSSQLConnectionOptions() {

    //example MSSQL_HOST=mku1xoy51v.database.windows.net:1433
    var host: string = process.env.MSSQL_HOST;
    var hostMatch: RegExpMatchArray = host.match(/^([^:]+)(?:[:]([0-9]+))?$/);

    var connectionOptions = {
        server: hostMatch[1],
        userName: "",
        password: "",
        options: {
            database: "",
            debug: {
                data: true,
                packet: true
            },
            encrypt: true,
            rowCollectionOnRequestCompletion: true,
            port: <string>undefined        
        },
    };

    if(hostMatch[2]) {
        connectionOptions.options.port = hostMatch[2];
    }

    return connectionOptions;
}

",
        options: {
            database: "gqq",
            debug: {
                data: true,
                packet: true
            },
            encrypt: true,
            rowCollectionOnRequestCompletion: true,
            port: <string>undefined        
        },
    };

    if(hostMatch[2]) {
        connectionOptions.options.port = hostMatch[2];
    }

    return connectionOptions;
}
