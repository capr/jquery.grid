## Dataset

### Constructor

	var d = dataset(options)

### Init

	d.fields <- [fi: {name:, client_default: v, server_default: v, ...}]
	d.rows <- [ri: row]; row = {values: [fi: val], attr: val, ...}
	d.fieldmap <- [fieldname1, ...]
	d.filter <- function(values, ri) -> true|false

	d.init()

### Events


	d.on(e, function(e, args...))  see [jQuery.on()](http://api.jquery.com/on/)
	d.trigger(e, args...)          see [jQuery.trigger()](http://api.jquery.com/trigger/)


### Fields

	d.fieldcount() -> n
	d.field(vfi) -> field
	d.move_field(svfi, dvfi)

### Rows

	d.rowcount() -> n
	d.row(vri) -> row
	d.insert(vri) -> added_row
	d.remove(vri) -> removed_row

	d.row_id(vri) -> id
	d.id_field_name <- name
	d.id_field_index <- index      (default 0)

### Values

	d.val(vri, vfi) -> val
	d.setval(vri, vfi, val) -> converted_val

	d.validate(val, field) -> throw ValidationError
	d.convert(val, field) -> val

	d.converters <- {<type>: function(val, field) -> val}
	d.validators <- {<type>: function(val, field) -> throw ValidationError(message)}
	d.ValidationError <- Error subclass

### Tree

	d.parent_id(vri) -> id
	d.parent_field <- name | index

	d.expanded(vri) -> true|false
	d.setexpanded(vri, expanded)
	d.collapse_all()
	d.expand_all()

### Changeset

	d.row_is_new(vri) -> true|false
	d.row_changed(vri) -> true|false
	d.val_changed(vri, vfi) -> true|false
	d.oldval(vri, vfi) -> val
	d.changes() -> { insert:, update:, remove:, }
	d.reconcile(results)
	d.apply_changes()
	d.cancel_changes()

### Remote

	d.url_path <- uri                 set to enable remote I/O
	d.url_args <- [arg1,...]          path components after url_path
	d.url_params <- {k1=v1,...}       url query params
	d.page <- n (default 1)
	d.page_size <- n (default 100)
	d.sort_expr() -> 'fieldname:asc|desc,...'
	d.url() -> url
	d.ajax([data], [success], [error])

	d.load([success], [error])
	d.save([success], [error])

