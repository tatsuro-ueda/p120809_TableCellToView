
u can wire from TableViewController to other view.

![ss](http://farm9.staticflickr.com/8435/7743974510_cd0be40eea_o.png)

For example, at first, you can set TableViewCell as below:

![ss](http://farm9.staticflickr.com/8284/7743986716_2ee222ac0d_o.png)

When tap the cell, the view with the number of tapped cell.

![ss](http://farm9.staticflickr.com/8297/7744080234_cf2be82f3b_o.png)

To send the number of tapped cell to next ViewController, you can use `performSegueWithIdentifier:sender:` and `prepareForSegue:sender` as below.

    - (void)tableView:(UITableView *)tableView didSelectRowAtIndexPath:(NSIndexPath *)indexPath
    {
        [self performSegueWithIdentifier:@"showDetail" 
                                  sender:[NSString stringWithFormat:@"%d", indexPath.row + 1]];
    }

    - (void)prepareForSegue:(UIStoryboardSegue *)segue sender:(id)sender
    {
        DetailViewController *c = segue.destinationViewController;
        c.string = (NSString *)sender;
    }

